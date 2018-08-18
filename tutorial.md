# Initial gatsby v2 project

1. `gatsby new gatsby-v2-google-sheets-netlify https://github.com/gatsbyjs/gatsby-starter-default#v2`
1. `cd gatsby-v2-google-sheets-netlify`
1. `git init`
1. (Create repository from the github interface)
1. `git remote add origin git@github.com:j-nolan/gatsby-v2-google-sheets-netlify.git`
1. `git push -u origin master`

# Create a Google service account

1. Create a [service account following these instructions](https://developers.google.com/identity/protocols/OAuth2ServiceAccount#creatinganaccount)
1. Download the configuration file and store it as `credentials.json` in your project's root directory

# Create the Google Sheet

1. (Create sheet in Google Drive)
1. Go to your spreadhseet in google drive, click "share" and add the service account user e-mail (you will find the service account e-mail the configuration file)

# Install gatsby-source-google-sheets

1. yarn add gatsby-source-google-sheets
1. In gatsby-config, add this to your plugin array:

```js
{
    resolve: 'gatsby-source-google-sheets',
    options: {
        spreadsheetId: 'get this from the sheet url',
        worksheetTitle: 'ie the name in the worksheet tab',
        credentials: require('./credentials.json')
    }
}
```

# Troubleshooting

I had the error "No key or keyFile set", couldn't figure it out. It was actually because I was trying to use a "simple" API key. You must use a "Service Account" Google API key or it won't work.
