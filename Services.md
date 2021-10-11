# Software as a Service
The term “software as a service” (or SaaS) mostly describes a licensing
model, where you can pay for the usage of some sort of online service.
Most of these software live in the cloud and provide various ways for the
end user to modify and query data in their systems. One example here is
Spotify, an online music streaming software, which end users can use to
listen to music and create their own playlist. Furthermore, Spotify has an
extensive software interface and packages which engineers can use to fetch
and modify data in the Spotify cloud programmatically.

# Service-oriented Architecture
Service oriented architecture (or SoA) is probably one of the favourite terms
in the industry. In simple terms, this style of architecture design supports
services more than anything. A service, as we learned above, needs to
serve some sort of business need and needs to be modeled around real
world requirements. Services need to be self contained and have a clean
interface with which they can be communicated with. They are deployed
and developed independently and represent a unit of functionality on an
abstract level. The architecture also involves the communication protocols
used between these services. Some software as a service companies use
service-oriented architecture to deliver quality products to their end users.

### Monolithic Service
One of the dreaded words of the decade for software engineers. Monolithic
applications and monolithic services are single services that grew too big
to be able to reason about. What “too big” means exactly will be one of the
core topics of this book. We will also see that this dreaded word does not
necessarily mean something bad.

## Microservice
The other dreaded word of the decade for software engineers (although,
for different reasons). A microservice, in short, is a service that lives in a
service-oriented architecture and is easy to reason about. These are loosely
coupled, lightweight components which have a well defined interface,
a single-purpose and are easy to create and dispose of. Due to the fine-­
grained nature, more people can work on them in parallel and ownership
of features becomes a cleaner problem to solve for the organization.
Now that we’ve taken a look at the high level definitions, let’s do a deep
dive into monoliths.

Understanding the Microservice
Just to recap: a microservice is a single purpose software application
that resides somewhere on the web, is a small-ish codebase and can be
reasoned about easily even by a single engineer.