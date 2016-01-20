#REST

Rest in an Architecture Style for distributed Systems. Whereas Soap used a post message with all the Info in the body, rest on the other hand **uses given HTTP protocoll (1.1) to serve an API**.

Rest doesn’t have to Serve JSON!

**Levels of Restfull**

Level 0 - No Rest
Level 1 - Resources
Level 2 - HTTP Verbs
Level 3 - Hypermedia Controls

make trade-offs: pure rest is most often not worth the effort

##Resources

- Entities or collections
- Tree structure
- URI as unique identifier

Examples:

```/users, users/toby, jobs/23```

##Methods

**Safe**

- GET
- HEAD
- OPTIONS
- TRACE

**Idempotent**

- POST
- PUT
- DELETE

**Safe** Must not change state
**Idempotent** Repeating must result in same state

Additional Methods: PATCH (Partial Update), COPY, MOVE

##Media Type

Media Types **assign semantic** to raw data

**Form**: type/subtype      … like text/html, image/png, application/vnd.adobe.flash-movie

###Media Type Headers

**define**


- What go get (Accept?)
- What to send (Content-Type?)
aka Content Negotiation



###XML vs JSON

XML

+More powerful
-More complex to consume
-More size (KB)

JSON
-Reduced feature set
+Easy to consume
+Less size (KB)

##Relations

**Hyperlinks** that Drive the workflow

##Error Handling

Error Status Code
4xx Client Error
5xx Server Error
Include explaining body