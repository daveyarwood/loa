# Facebook

Facebook has a "Graph API" that allows you to get a variety of data. In order to use it, you have to obtain a user access token, which apparently you can't do unless you use the login dialog, via their JavaScript SDK. (That's the thingy that pops up and asks you if you want to authorize this application to access your facebook account.)

Good advanced tips here: https://developers.facebook.com/docs/graph-api/advanced

For example, you can receive API updates via webhooks, instead of continuously polling Facebook's servers. There is also rate limiting, so this is probably a good idea.

## Home Feed

Unfortunately, they deprecated the "home feed" endpoint in October 2015. It seems like they want to restrict developers from showing the home feed, unless they're making a Facebook-branded feed application.

There is a Public Feed API that looks useful, but is restricted to a limited set of media publishers with prior approval by Facebook, and you can't apply to use it, so that's off the table.

That's probably OK, though, as your Facebook home feed is a provider of distractions, probably not in line with the mission statement of LOA. The notification feed (things you need to see, like events someone invited you to, messages from people, posts on your timeline or that you've been tagged in, friend requests, etc.) seems more relevant, and that kind of information is available via the Graph API.

If we really do want to see the home feed, we could possibly get around the limitations by using a headless browser (with the user already signed into facebook), going to the user's feed, and parsing the content on the page. It seems like this might be tricky for the desktop site, as it looks like they dynamically generate random class names. That's not the case for their mobile site, though. There is a `section.storyStream` DOM element containing one `article` element per post.

Example facebook mobile site scraper: https://gist.github.com/ganglio/4276763

## Notification Feed

It doesn't look like you can directly query unread notifications unfortunately (that would have been the easiest route), but you can query for specific things like posts on your timeline, events you've been invited to, etc. So, we can query for that information and then make our own feed out of it, and have our own read vs. unread system if we really want it. So far, I'm thinking it will be enough to just have a minimal feed that the user can keep up with (just important things requiring his/her attention).

# Twitter

They have a nice REST API allowing you to access things like mentions and direct messages, as well as the user timeline and the home timeline. Like Facebook, this also requires some setup with the user authorizing the application to access his/her Twitter account.

See: https://dev.twitter.com/rest/public

They also have a Streaming API, which could be handy if we want to update the feed in real time without polling the REST endpoints.

Twitter actually recommends using a combination of both APIs, depending on the needs of your application. I think at least at first, we can just poll the REST endpoints and refresh on demand.

There is rate limiting. They recommend caching results instead of fetching them on every page load.
