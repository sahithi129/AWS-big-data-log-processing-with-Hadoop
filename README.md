# AWS-big-data-log-processing-with-Hadoop

Project Steps:

1. Set up prerequisites for our cluster:

  1.1 You should sign up for AWS Account, or Sign In if you have one.

  1.2 Create key-pair in EC2 dashboard to use in EMR cluster instances in next steps.

  1.3 Create an S3 Buckets and name it your choice example and then separate folders:
      1.3.1 Create Folder --> Code : To save Hive scripts.
      1.3.2 Create Folder --> Code : To save Input data files
      1.3.3 Create Folder --> Code : To save Output results

2. Launch a fully functional Hadoop cluster using Amazon EMR.
  2.1 Sign in to the AWS Management Console and open the Amazon EMR console at https://console.aws.amazon.com/elasticmapreduce/.

  2.2 Choose Create cluster.

  2.3 On the Create Cluster - Quick Options page, accept the default values except for the following fields:

  2.4 Enter a Cluster name that helps you identify the cluster, for example, My First EMR Cluster.

  2.5 Under Security and access, choose the EC2 key pair that you created in previous step.

  2.6 Choose Create cluster.

3. Create a HIVE Script and Save it in S3 -> your-bucket -> Code

4. To run the Hive script by submitting it as a step

  4.1 Open the Amazon EMR console at https://console.aws.amazon.com/elasticmapreduce/.

  4.2 In Cluster List, select the name of your cluster. Make sure the cluster is in a Waiting state.

  4.3 Choose Steps, and then choose Add step.

  4.4 Configure the step according to the following guidelines:

    4.4.1 For Step type, choose Hive program.

    4.4.2 For Name, you can leave the default or type a new name. If you have many steps in a cluster, the name helps you keep track of them.

    4.4.3 For Script S3 location, type s3://region.elasticmapreduce.samples/cloudfront/code/Hive_CloudFront.q. Replace region with your region identifier. For example, s3://us-west-2.elasticmapreduce.samples/cloudfront/code/Hive_CloudFront.q if you are working in the Oregon region. For a list of regions and corresponding Region identifiers, see AWS Regions and Endpoints for Amazon EMR in the AWS General Reference.

    4.4.4 For Input S3 location, type s3://region.elasticmapreduce.samples

    4.4.5 Replace region with your region identifier.

    4.4.6 For Output S3 location, type or browse to the output bucket that you created in Create an Amazon S3 Bucket.

    4.4.7 For Action on failure, accept the default option Continue. This specifies that if the step fails, the cluster continues to run and processes subsequent steps. The Cancel and wait option specifies that a failed step should be canceled, that subsequent steps should not run, abut that the cluster should continue running. The Terminate cluster option specifies that the cluster should terminate if the step fails.

  4.5 Choose Add. The step appears in the console with a status of Pending.

  4.6 The status of the step changes from Pending to Running to Completed as the step runs. To update the status, choose the refresh icon to the right of the Filter. The script takes approximately a minute to run.

5. View the Results

  5.1 Open the Amazon S3 console at https://console.aws.amazon.com/s3/.

  5.2 Choose the Bucket name and then the folder that you set up earlier. For example, mybucket and then MyHiveQueryResults.

  5.3 The query writes results to a folder within your output folder named os_requests. Choose that folder. There should be a single file named 000000_0 in the folder. This is a text file that contains your Hive query results.

  5.4 Choose the file, and then choose Download to save it locally.

  5.5 Use the text editor that you prefer to open the file. The output file shows the number of access requests ordered by operating system. The following example shows the output in WordPad:

