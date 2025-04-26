## Pull Upload via Vimeo API

[![DOI](https://zenodo.org/badge/973096294.svg)](https://doi.org/10.5281/zenodo.15286574)

The pull method offers a convenient mechanism for incorporating video content into the Vimeo platform by referencing an existing online resource. This approach requires providing a valid URL that directs Vimeo's systems to the desired video file. Once we get this info, Vimeo's infrastructure will automatically retrieve a copy of the content, allocate appropriate storage within Vimeo, and manage it in a manner consistent with directly uploaded media. Furthermore, Vimeo's system is engineered to manage potential network interruptions during the retrieval process, ensuring a robust and reliable operation. The fundamental requirement for utilising this method is the precise and complete URL of the target video file.

Important Note: For video assets hosted on a CDN, it is essential to ensure that the provided URL grants public access without requiring specific authentication. Alternatively, for enhanced security, pre-signed URLs may be employed.

Where the requisite URL is readily available, the pull method presents a relatively straightforward integration pathway with Vimeo. However, its efficacy is predicated on the prior existence and accessibility of the video file at the specified network location. While this approach may prove advantageous for certain integration scenarios with Vimeo, the "tus" and "POST" methods often provide greater flexibility and broader applicability for a wider range of applications.

The process, mirroring a simplified curl command, is illustrated in the following UML sequence diagram:

~~~```bash
curl -i -X POST \
  -H "Authorization: Bearer {TOKEN}" \
  -H "Content-Type: application/json" \
  -H "Accept: application/vnd.vimeo.*+json;version=3.4" \
  -d '{
    "upload": {
      "approach": "pull",
      "link": "{URL}"
    },
    "name": "{name}"
  }' \
  "https://api.vimeo.com/me/videos"
~~~

![image](https://github.com/user-attachments/assets/cf37cf56-6f9f-4e7d-b1fb-db03e8e2ab52)
