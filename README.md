# aws-srcds
Repo for resources launching and managing Valve's Source Engine Dedicated Servers on AWS

This is a very, very low-frills cloudformation template to stand up a Pure TF2 server into its own VPC. In order to use this, you'll need the following prerequisites:

- An AWS Account
- An AWS EC2 Keypair

And that's it.

I tried to create the template so it's super easy to use, and you don't need to have much AWS experience, or pre-existing infrastructure, in order to get a TF2 server up and running. The template will do everything for you - just head over to the CloudFormation service page and create a new stack. You'll need to upload the template and give the stack a name. Provide your EC2 Keypair name in the parameter slot provided. You can leave the defaults for the rest of the parameters, and you should be ready to play in under 10 minutes.

I've tried to make sure running costs are as low as possible, but you'll be paying the on-demand hourly rate for an m5.large instance for as long as the stack is up. In my region, Sydney, that's currently $0.12 per Hour.

The server should appear in the server browser in game. If not, look for the instance's public IP address. the game server runs on the default port.

Once you're finished with your session, just delete the stack and you're done.
