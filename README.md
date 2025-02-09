# Rave Base Assets

This repository contains HTML templates and static files that can be easily modified and customized according to customer specific needs. You can fork this repository and make changes to the templates to tailor them to your requirements.

## Usage

1. Fork this repository to your own GitHub account.

2. Configure the full name of your forked repository in the **Settings > Templates** section of the Developer Portal. This is necessary to set up the correct authorization for deployment automation.

   > **Note**
   > The full name of a GitHub repository consists of your GitHub account username followed by the name of the repository, separated by a forward slash ("/"). For example, if your GitHub account username is "your-company" and you named your forked repository "my-custom-templates", the full name would be "your-company/my-custom-templates".

   > **Warning**
   > It's important to ensure that the repository is protected from unauthorized changes. This may involve setting up branch protection rules, access permissions, or enabling required reviews for pull requests. By doing so, you can ensure that only authorized individuals can make changes to the repository and maintain control over the deployment process. Reach out to the Rave Support Team if you need help configuring the appropriate repository settings.

3. Clone the forked repository to your local development environment.

    ```shell
    git clone https://github.com/<your-account>/<your-fork-name>.git
    ```

4. Modify the HTML template or static images files located in the repository according to your needs.
5. The repository uses a workflow action to automatically publish changes whenever a commit is pushed to a release branch. To enable this automation, certain environment variables need to be set in the repository settings. These variables are required for authentication and configuration of the publishing process, and you may find them under the **Settings > Templates** section of the Rave Developer Portal.

   > **Note**
   > See [Creating configuration variables for a repository](https://docs.github.com/en/actions/learn-github-actions/variables#creating-configuration-variables-for-a-repository) or [Creating configuration variables for an environment](https://docs.github.com/en/actions/learn-github-actions/variables#creating-configuration-variables-for-an-environment) for instructions on how to configure those.

   - `GCS_BUCKET`: The customer bucket that will hold the assets files.
   - `SERVICE_ACCOUNT_EMAIL`: e service account email to use for authentication.
   - `WORKLOAD_IDENTITY_PROVIDER`: The workload identity provider for authentication and authorization.

6. Publish Changes:

   - Enable GitHub actions on your project. You can do this by navigating to the "Actions" tab and ensuring that workflows are enabled. Note that workflows are initially disabled by default on forks.
   - For changes to be automatically published, a commit needs to be pushed to a branch with a prefix of `release-` following the branch naming convention: `release-environment-name`. For example: `release-develop`.  Your deployment branch may be found under the **Settings > Templates** section of the Rave Developer Portal.
   - Push your changes to the appropriate release branch.

7. Deployment:

   - Your application should be configured to fetch the latest templates from the repository based on the specific environment branch. Ensure that your deployment process includes pulling the latest changes from the desired release branch.

## Assets Structure

The repository is structured as follows:

- 📂 **templates**: This folder contains web page layouts, such as the reset password page. You can modify the HTML files in this folder to customize the visual appearance and base structure of your web pages.

- 📂 **templates/email**: This folder contains templates specifically designed for sending emails. Each email template consists of an HTML file and a corresponding plain text (TXT) file. The HTML file represents the actual email content, while the plain text file serves as the email body for clients that do not support HTML rendering. Please refer to the documentation in each HTML file for information on what is available on each template.

- 📂 **templates/static/images**: This folder contains static images that are used across the HTML templates. Any image files you want to include in your templates should be placed in this folder. You can reference these images in your HTML templates to display logos, icons, or other visual elements.


## Contributing

If you find any issues or have suggestions for improvements, feel free to open an issue or submit a pull request. We appreciate your contributions!

## License

This repository is licensed under the [MIT License](LICENSE).
