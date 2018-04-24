# The Stacks - static-web-ui

## FAQ

### How do I update the Continuous Deployment script?
The continuous deployment is done by AWS CodePipeline and CodeBuild via the buildspec.yml file.

Take a look at the buildspec.yml file.  https://docs.aws.amazon.com/codebuild/latest/userguide/build-spec-ref.html#build-spec-ref-syntax

### How do I enable SSL (https)?
Update the pipeline CloudFormation stack and set the `Protocal` input parameter to `HTTPS`.  

You must approve the domain validation email AWS sends.  See https://aws.amazon.com/certificate-manager/faqs/

### When I request a certificate which email addresses is the certificate approval request sent?

When you request a certificate using email validation, a WHOIS lookup for each domain name in the certificate request is used to retrieve contact information for the domain. Email is sent to the domain registrant, administrative contact, and technical contact listed for the domain. Email is also sent to five special email addresses, which are formed by prepending admin@, administrator@, hostmaster@, webmaster@ and postmaster@ to the domain name you’re requesting. For example, if you request a certificate for server.example.com, email is sent to the domain registrant, technical contact, and administrative contact using contact information returned by a WHOIS query for the example.com domain, plus admin@server.example.com, administrator@server.example.com, hostmaster@server.example.com, postmaster@server.example.com, and webmaster@server.example.com.

The five special email addresses are constructed differently for domain names that begin with "www" or wildcard names beginning with an asterisk (*). ACM removes the leading "www" or asterisk and email is sent to the administrative addresses formed by pre-pending admin@, administrator@, hostmaster@, postmaster@, and webmaster@ to the remaining portion of the domain name. For example, if you request a certificate for www.example.com, email is sent to the WHOIS contacts, as described previously, plus admin@example.com rather than admin@www.example.com. The remaining four special email addresses are similarly formed.

After you request a certificate, you can display the list of email addresses to which the email was sent for each domain using the ACM console, AWS CLI, or APIs.