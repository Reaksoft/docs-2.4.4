# SAML
## Overview
SAML is an XML-based, open-standard data format for exchanging 
authentication and authorization data between an identity provider 
(like the Gluu Server) and a service provider (like Dropbox, O365, etc.). 
SAML is a stable and mature standard, and is well supported at many of the 
Internet's largest domains. However, the last major release of SAML was in 2005! 
Therefore it is important to understand when to use SAML and when to use a 
newer protocol like OpenID Connect to achieve your identity goals. 

In short, refer to these four considerations to determine which protocol 
to use for single sign-on (SSO):

- If you have an application that already supports SAML, use SAML.
- If you need to support your customers or partners authentication requirements, use SAML.
- If you have a mobile application, use OpenID Connect.
- If you are writing a new application, use OpenID Connect.

If you are continuing with this SAML documentation it is presumed 
that your use case aligns with one or both of the first two bullet points above. 
If not, we recommend that you review the [OpenID Connect](./openid-connect.md) 
portion of the Gluu Server docs. 

The Trust Relationship(TR) is added by clicking the `Add` button located in the lower left side of the page.     

### Relying Party Configuration     
If the target application does not already support SAML, the Relying Party software must be configured. The relying party configuration is accessible on the TR Creation page. The checkbox `Configure specific Relying Party` must be checked.     

![enable-relying-party.png](../img/saml/enable-relying-party.png)     

The checkbox will result in a link which can be accessed to find information about configuring the relying party for the TR. The image below shows the relying party config panel from which the administrator can add the specific option.     

![tr-relying-party](../img/saml/tr-relying-party.png)     

!!! Note     
    If the target application does not already support a federation standard like SAML, and you or the developer are planning on adding federation to the application, we strongly recommend using OpenID Connect rather than SAML. OpenID Connect is newer, easier to use, and follows modern best practices. Learn more in our blog: [OAuth vs. SAML vs. OpenID Connect](http://gluu.co/oauth-saml-openid).
    
### Federation Configuration     
If the SP is part of an identity federation such as InCommon, the administrator must add the federation as an SP in the Gluu Server. This will enable the administrator to more easily create TRs with SPs in the federation. The example below shows how an administrator would add a TR for the InCommon Federation.

![federationTR](../img/saml/federationTR.png)

Once a TR has been established with the federation, the Gluu Server administrator can easily create TRs with any SP included in the federation by selecting the federation from the `Federation Name` drop down menu and selecting the entity-id for the SP.

![federation-entityid.png](../img/saml/federation-entityid.png)
