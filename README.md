# Pardot's Export Activities - APEX Implementation

This project supports a series of blog posts on thespotforpardot.com (still to be published) around Pardot External Activities.

## Installation & Usage
It is important to note that this APEX code cannot work by itself. It requires a Named Credential properly configured to communicate with Pardot. If you aren't interested in reading the complete series of blog posts (recommended), then please at least follow the steps in our [Connecting to Pardot API from APEX](https://thespotforpardot.com/2021/02/02/pardot-api-and-getting-ready-with-salesforce-sso-users-part-3a-connecting-to-pardot-api-from-apex/) blog post which details those steps.

Once the Named credential is good to go, it is time to tweak the APEX code in this project, deploy, and then you are good to go.

## APEX Tweaks Required
At a minimum, you will need to modify the value of `ONLY_ONE_BUSINESS_UNIT_ID` to be **your** Pardot Business Unit Id. Making this change, this code base will support an org with only one Pardot Business Unit.

**Recommended** - you should take a look at the try/catch block to see how you will want to handle any potential API errors.

### Working with Multiple Business Units
This is where things get challenging, and your approach may vary depending on business case. Approaches may include:

- Include Business Unit ID as a Parameter to the Action, let the Flow designer worry about selecting the right one
- Iterate PardotTenant to find the correct Business Unit Id(s)

This code sample includes a set of commented-out code for handling the first approach. To leverage it, remove all code references to `ONLY_ONE_BUSINESS_UNIT_ID` and then un-comment-out the code that references `businessUnitId`. Once deployed, any Flows that existed prior will need to be modified.