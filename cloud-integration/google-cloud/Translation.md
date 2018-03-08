---
title: Google Cloud Translation API
page_title: Google Cloud Translation API
slug: common-google-cloud-translation
position: 4
---

## Google Cloud Gognitive Services

Gognitive computing or cognitive services are platforms that are powered by artificial intelligence and signal processing. These services provide you with the possibility to directly use different scientific breakthroughs such as machine learning, natural language processing and speech/vision recognition. 

In this article we are going to show you how to use Google's Translation API. The process  of embedding the functionality in your .NET application is very easy once you have enabled the feature from your GCP console.

### Using the Translation API

You can use the Translation Cognitive services to translate messages or any text on different languages within your application.

In order to proceed with adding the functionality in your application, you should first enable the feature from your GCP console.

Once you have done so, you can add the **Google.Cloud.Translation.V2 NuGet** package to your application as shown in the image below:

![](../images/google-cloud-translation-api.png)

Once you have all the required packages installed, you can use it within your application by utilizing the **TranslationClient** class.

We are going to use the following setup:

![](../images/translation_before.png)

The typed message will be translated on a click of a RadButton. The following snippet shows how to access the translation API and translate the specific text:

	private async void TranslateMessage(object sender, EventArgs e)
        {
            string textToTranslate = this.inputEntry.Text;

            if (!String.IsNullOrEmpty(textToTranslate))
            {
				//authJson represents the unique json issue by Google Cloud used for authentication
                var credentials = GoogleCredential.FromJson(authJson);
                TranslationClient client = TranslationClient.Create(credentials);
                var response = client.TranslateText(textToTranslate, "ru") as TranslationResult;
                this.outputLabel.Text = response.TranslatedText;
            }
        }

>note The example shows how to create the TranslationClient by feeding it with your credentials. However, you can also set up the authentication on your machine and there will be no need of such steps. You can refer to Google's [Authentication Overview](https://cloud.google.com/docs/authentication/) section.

Here is the result of the operation:

![](../images/translation_after.png)

## See Also

- [Google Cloud Overview]({%slug common-google-cloud-overview%})
- [Google Cloud Functions]({%slug common-google-cloud-functions%})
- [Google Cloud MySQL DataBase]({%slug common-google-cloud-mysql%})