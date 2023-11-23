# trusted-runner-spec
A specification for a GitHub Actions self-hosted runner that you can trust.  
If you don't care about blabla, you can head directly to the [specification](SPEC.md). If you want to understand / challenge the rational, go through the below paragraphs. 
<br/><br/>  

## Context and motivations
### Software factory rational
Let's first tackle what is obvious: CI/CD practices are a requirement of any activity within software industry, because of efficiency, quality and security it adds to software delivery. Software factory (sf) is the enabler of CI/CD practices. 
<br/><br/>
  
### Software factory as a service
Now, let's take a look at the sf within a professional context. As of today, anybody can (quite easily) implement a software factory thanks to solutions such GitHub. The independant developer working on a mobile app can setup within minutes a new CI/CD chain. 

When it comes to corporate context, sf is usually getting implemented as a corporate service. As any service, it has a provider and a consumer. Depending on the structure in which sf is delivered, provider-consumer relationship can be very different. 
- In small company, provider and consumer can belong to the same team and work next to each other.
- If you move to larger organization, provider and consumer might belong to different teams, sitting in distant location, living in different timezones, and the number of consumers can get far larger than the team that is providing sf. 
<br/><br/>  

### Focus on financial institutions
Financial institutions are a regulated context, it means it must comply with laws and rules defined by the regulators (e.g. ECB). When it comes to compliance, things don't work on a trust relationship basis. Regulated actor must prove to regulator that it complies. This brings a significant shift in the way actors within a company are interacting. When an evidence must be provided, it can't rely on a simple declaration, it must rely on a unquestionable audit track.  
<br/>  

That being said, let's apply this to the software development activity and more specifically to the build process. If someone cares about the security and the resiliency of your application, he should look to what happened within software factory. And lets be clear about this, now, the regulator cares about the way financial institutions are building software. 
<br/><br/>  

### So, what's the story ?
When you send your code to a software factory, what mainly happens is:
- your code is built to produce deployable artifacts
- your code is inspected for quality and security
- your code is tested
- the dependencies of your code are reviewed
- your code (e.g. the artifacts build upon your code) is deployed

More things can happen, and more things actually happen, but the steps listed above are the ones that will matter to prove you are building a secured application. 
Major problem is that most Continuous Integration systems (CI) are a wide freedom space for developers. 
And that's pretty cool for developers. 
But for people who must prove that good job was done, it's a nightmare. 
And in regulated industries, sf service provider is asked to prove. 
<br/><br/>  

### You mentionned freedom space, what are you refering to ?
SHELL STEP WITHIN A PIPELINE
<br/><br/>  

### Why ?
because the developer can (intentionally or not) build black box using shell step and break auditability. 
<br/><br/>  

### So, should we prevent shell steps within CI ?
NO NO (I'm a developer too). More seriously, CI is an innovation place, and preventing developer from putting his hands in it is as benificial as jumping on the brake 100 yards from the finish line. 
<br/><br/>  

### So ?
Let's try to imagine a system in which the sf service provider can guarantee execution of particular steps that will be used as evidence for regulator, while still allowing developer to configure his pipeline. 
<br/><br/>  

## The place to be

What is the best place to control what's going on in a software factory ?
- the code -> NO
- the CI controller -> NO
- the CI build agent -> YES YES YES
<br/>

GitHub Actions is a great CI system that provides a large autonomy to developer. 
The purpose of this specification is to tell how we can conciliate this great tool with sf service provider concerns. Now let's move to the [spec](SPEC.md). 
<br/><br/>  

