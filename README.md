## README.md
![Logo](aws_sam_introduction.png)
# TEMPLATE INSTRUCTIONS
I'm making this guide with the assumption that the user has only entry-level familiarity with AWS to make it accessible.
This guide also assumes you have a Route53 Domain and vaild certificate available

To use this template install AWS cli and SAM cli, it's important that you have both.

### Don't forget to edit them template to fit your needs!
You can get help [Cloudformation](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-template-resource-type-ref.html) and [SAM](https://github.com/awslabs/serverless-application-model/blob/master/versions/2016-10-31.md)

To test your API using SAM local:
1. Run this code in your terminal or command prompt:
    ```console
    sam local start-api 
    ```
2. Use curl or some other tool to test your API's inputs and outputs:
    ```console
    curl domain.com
    ```

To deploy your template to AWS properly:
1. Edit the template to suit your needs. 
2. Create a bucket that you're happy to store code artefacts in.   
3. Change the bracketed values with what's specified.
4. Run this code in your terminal or command prompt:
    ```console
    aws cloudformation package --template-file template.yaml --s3-bucket (name of artefact bucket) --output-template-file output.yaml --parameter-overrides DomainName=(domain name) Certificate=(certificate ARN)
    aws cloudformation deploy --template-file output.yaml --s3-bucket (Same bucket as above) --stack-name (name of stack) --capabilities CAPABILITY_IAM
    ```
5. Check Cloudformation to ensure that your stack was successfully created.
6. Have fun with AWS!