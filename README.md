# Deploying a Streamlit application on AWS: An end-to-end tutorial

It's a simple application that is currently using Stream as the front-end. Take this existing Streamlit app and deploy it on AWS 

## Get started

> Before deploy the Streamlit app, make sure it works locally

- Launch a Amazon EC2 instance using free tier

- Install all the required libraries/packages

- Run Streamlit app

- Open the app on the browser

- Point domain name to the AWS EC2 Linux instance

1. Launch an Amazon EC2 instance

- Before start with using the amazon ec2 instance, setup the AWS account. Sign up with an email ID and set up the payment information on the AWS website. Works just like a simple sign-on. Assume that have an AWS account and follow through the essential steps.

- Go to AWS Management Console using https://us-west-2.console.aws.amazon.com/console.

- On the AWS Management Console, select “Launch a Virtual Machine”. Here set up the machine where to deploy our Streamlit app.

- In the first step, choose the AMI template for the machine. Select the 18.04 Ubuntu Server since it is applicable for the Free Tier. And Ubuntu.

- In the second step, Select the t2.micro instance as again it is the one which is eligible for the free tier. As one can see t2.micro is just a single CPU instance with 512 MB RAM. Opt for a bigger machine if dealing with a powerful model or are willing to pay.

- Keep pressing Next and then configure Security Group tab. Need to add a rule with Type: “Custom TCP Rule”, Port Range:8501, and Source: MyIP. Use the port 8501 here since it is the custom port used by Streamlit.

- Click on “Review and Launch” and finally on the “Launch” button to launch the instance. Once Click on Launch might need to create a new key pair

- Go to your instances to see if the instance has started. Hint: See the Instance state, it should be showing “Running”

- Select the newly created instance, and copy the Public DNS(IPv4) Address from the description. It should be something starting with ec2.

2. Install all the packages/dependencies

After all the above steps one should be able to see the ubuntu prompt for the virtual machine. Set up this machine to run our app using this app as following for the demonstration purposes

```
$ git clone https://github.com/AIBIZSERVICE/StreamlitonAWS.git
$ cd StreamlitonAWS
```

```
$ sudo apt update
$ sudo apt get install -y python3-pip
$ pip3 install -r requirements.txt
$ export PATH=~/.local/bin/:$PATH
$ echo "export OPENAI_API_KEY='yourkey'" >> ~/.zsh
$ source ~/.zsh
$ echo $OPENAI_API_KEY

Once the dependencies are installed without any errors, the machine is now prepped and ready to run.

- Running Streamlit on Amazon ec2

```
streamlit run app.py
```
After running the streamlit, find the following ip address (in your case it is different)

```
View your Streamlit app in your browser.

  Network URL: http://172.31.41.84:8501
  External URL: http://18.224.200.50:8501
```

3. Open the app on the browser

Now go to a browser and type the external URL to access the app. In this case the address is http://18.224.200.50:8501. Here is the output. This app will be up right now if start play with it.


4. Run Streamlit in the background

Use 'screen' or 'tmux' to run streamlit in the background


5. Associate domain to Amazon EC2 instance (Optional)

Here are an example of brief [instructions](https://u.osu.edu/walujo.1/2016/07/07/associate-namecheap-domain-to-amazon-ec2-instance/) 
