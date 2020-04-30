# TF2 server on AWS

## What's all this then?
This repo contains cloudformation templates to create Team Fortress 2 dedicated servers running on AWS. This enables you to create your own public or private game servers using Amazon's Elastic Compute Cloud (EC2) service. You can then host online gaming sessions for a few cents per hour.

## Alright, I'm on board
Cool! The templates were created at the height of the 2020 Covid-19 pandemic. I created them to be as easy to use as possible by folks who like gaming, but don't necessarily have a lot of technical experience: either in general or specifically with AWS. In making the template easy to use, I've sacrificed some configuration flexibility of the server itself. You'll get a **pure** (sv_pure 2) TF2 server with a default configuration. If you want something more specialised, you'll need to dig into the template and modify the server.cfg file, but that's way beyond the scope of v1.0.

If you're non-techie, start with the **Quickstart** section.

If you're more technically-inclined and want to get into the nuts and bolts, Head to **Detailed Setup**

# Disclaimer
**Using this cloudformation template to create a stack in your AWS account will incur charges that you are responsible for! By using this template you absolve me of any responsibility for any charges whatsoever. That's all on you. Don't forget to delete the Cloudformation stack once your gaming session has finished otherwise you'll keep being charged the hourly costs for the various resources that are created by the stack**

I've tried to make sure running costs are as low as possible, but you will be paying the on-demand hourly rate for an m5.large instance for as long as the stack is up. In my region, Sydney, that's currently $0.12 per Hour.

For this reason, you should get familiar with the method of [deleting a Cloudformation stack](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/cfn-console-delete-stack.html) before you get started.

# Quickstart
This section is designed to get you up and running as quickly as possible with as few pre-requisites and configuration changes as possible. If you're reading this, you just want to get in there and start blasting without thinking about it too much.

## Pre-Requisites
The following pre-requisites are absolutely required in order to use this template. If you don't follow these steps, you won't get very far.

### 1. AWS Account
You definitely need an AWS account in order to create AWS resources such as this server.

If you do not already have an AWS account, [Follow these instructions](https://aws.amazon.com/premiumsupport/knowledge-center/create-and-activate-aws-account/) to create one.

If you already have an AWS account, you don't need to create a new one to use this template.

## Getting Up and Running

In order to get up and running, you need to [create a cloudformation stack](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/cfn-console-create-stack.html) using the template:

1. Sign in to your AWS Account.

2. Navigate to the Cloudformation Service page by typing _Cloudformation_ into the **Find Services** box. Click the link that appears beneath your typed text.

3. a) If this is your first time creating a Cloudformation stack in this AWS account, you'll be greeted with the CloudFormation service homepage. Click the orange button titled _Create stack_. b) If you've created other stacks previously, you'll be greeted with a list of your existing Cloudformation stacks. Click the _Create stack_ button at the top-right, then select _With new resources (standard)_ from the drop-down.

4. On the resulting page, firstly click the _Upload a template file_ option. This will display the _Choose file_ button, which you'll need to click. Navigate to the location of the template file and select it. Once done, an auto-generated S3 URL will be displayed in the bottom of the screen. Click the orange button labelled _Next_

5. This page allows you to specify a stack name and template parameters. The only thing that's **required** is the _Stack name_, which you can enter at the top of the screen. Note the limits on characters that can be used (i.e. no spaces).

6. (Optional) You might also want to provide a different value for the _Server Hostname_ parameter. This is what appears in the TF2 server browser. If you don't want this to be a public server, provide a _Server password_. Don't get too fancy with this - I haven't done extensive testing on which characters are allowed and whether use of non-alphanumerics will break my dodgy bash scripts ;)

7. Once you've provided a server name and optional parameters, click the orange _Next_ button.

8. The next page is the _Configure stack options_ page. Scroll to the bottom and hit the orange _Next_ button.

9. The next page is the _Review Stack_ page. Scroll to the bottom and check the checkbox in the blue-highlighted section labelled _I acknowledge that AWS CloudFormation might create IAM resources._. **you must check this box or stack creation will fail**. Once you've checked the box, hit the orange _Create Stack_ button.

10. You'll be navigated to the stack page, and your stack will be highlighted with the status CREATE_IN_PROGRESS. If you're super-keen, you can repeatedly click the refresh button on the right in order to track the creation progress of each resource defined in the stack. Eventually, after about 6 minutes, stack creation will complete, and the state will change to CREATE_COMPLETE in green with a little check mark. This is a happy place to be.

11. Click the _outputs_ tab to view the outputs of this stack. One of the outputs is the **ServerHostname**. This is what appears in the server browser in-game. If you've kept the default, it'll be _My Awesome TF2 Server_. If, for some reason, you can't see your server in the server browser, you can connect directly using the public IP address. This is presented as the _PublicIPAddress_ output value.

# Detailed Setup
_coming soon_