---
title: "Experiments with Congress.gov API"
date: 2022-09-11T12:00:00-08:00
draft: false
tags: 
    - API
    - Congress
    - Gov
    - Bills
    - Congress.gov
    - Congress.gov API
---

![](/congress.png)

[This September](https://www.congress.gov/help/enhancements) Congress.gov released a neat new API!

> Congress.gov shares its application programming interface (API) with the public to ingest the Congressional data. [Sign up for an API key](https://api.congress.gov/sign-up/) from api.data.gov that you can use to access web services provided by Congress.gov. To learn more, view our [GitHub](https://github.com/LibraryOfCongress/api.congress.gov/) page.


It is possible to experiment with the API by signing up and then entering the key in the authorization dialog at the top of the page. From there, you will see [cURL](https://curl.se/) commands made for example:

```
curl -X GET "https://api.congress.gov/v3/bill?format=json&api_key=KEYHERE" -H "accept: application/xml"
```

Example Bills item in response back, as a 200:

```
{
  "bills": [
    {
      "congress": 117,
      "latestAction": {
        "actionDate": "2022-09-09",
        "text": "Placed on the Union Calendar, Calendar No. 354."
      },
      "number": "1456",
      "originChamber": "House",
      "originChamberCode": "H",
      "title": "Peace Corps Reauthorization Act of 2022",
      "type": "HR",
      "updateDate": "2022-09-12",
      "updateDateIncludingText": "2022-09-12T17:15:22Z",
      "url": "https://api.congress.gov/v3/bill/117/hr/1456?format=json"
    },
    [CONTINUED...]
```

# My experiment

I wanted to create a simple application that would retrieve a list of bills and then show a summary of that particular bill. In a later edition, I made it so you could click through the list of bills. 

[The Github Repo for this whole project is here.](https://github.com/airbr/getABill)

The parts of the Express JS server that does the work with the API looks just like this:

```
app.get('/bill/:offset', (req, res) => {

    if (req.params.offset){
        var offset = 20 * req.params.offset;
    }

    request(
        { url: 'https://api.congress.gov/v3/bill?format=json&api_key='+ process.env.KEYSTOCONGRESS + '&offset=' + offset },
        (error, response, body) => {
          if (error || response.statusCode !== 200) {
            return res.status(500).json({ type: 'error', message: err.message });
          }        
          res.json(JSON.parse(body));
        }
      )
});

app.get('/summary/:congress/:type/:number', (req, res) => {
    request(
        { url: 'https://api.congress.gov/v3/bill/'+ req.params.congress + '/'+ req.params.type + '/'+ req.params.number + '/summaries?format=json&api_key='+process.env.KEYSTOCONGRESS },
        (error, response, body) => {
          if (error || response.statusCode !== 200) {
            return res.status(500).json({ type: 'error', message: err.message });
          }        
          res.json(JSON.parse(body));
        }
    )
});
```

# Deployment example

I created a [REPL.co deployment](https://replit.com/@airbr/Get-a-Bill-from-Congress#index.html) of my project which anyone can view and fork: 

<div class="" style="height: 600px; width: 100%;">
  <iframe
    src="https://get-a-bill-from-congress.airbr.repl.co/"
    title="get-a-bill-from-congress on repl.co"
    allow="geolocation; microphone; camera; midi; encrypted-media; xr-spatial-tracking; fullscreen"
    allowFullScreen
    style="height: 100%; width: 100%; border: 0;">
  </iframe>
</div>


# Conclusion

I really enjoyed experimenting with this API. I share this hopeful that it will help someone else experiment.