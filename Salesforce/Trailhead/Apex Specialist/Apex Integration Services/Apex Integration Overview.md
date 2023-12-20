<h2 align=center>Apex Integration Overview</h2>

<b>Be sure Remote Site Settings have been added</b><br>
Add two Remote Sites to the Remote Site Settings to allow callouts to external sites.

**Prework**: If you already added the Remote Sites as directed in the unit then you are ready to verify.
* Add a Remote Site
  * Name: animals_http
  * Remote site URL: https://th-apex-http-callout.herokuapp.com
  * Description: Trailhead animal service: HTTP
* Add a Remote Site
  * Name: animals_soap
  * Remote site URL: https://th-apex-soap-service.herokuapp.com
  * Description: Trailhead animal service: SOAP
 
**Solution-**
Authorize both of these endpoint URLs by following these steps.

1. From Setup, enter Remote Site Settings in the Quick Find box, then click Remote Site Settings.
2. Click New Remote Site.
3. For the remote site name, enter animals_http.
4. For the remote site URL, enter https://th-apex-http-callout.herokuapp.com.
5. This URL authorizes all subfolders for the endpoint, like https://th-apex-http-callout.herokuapp.com/path1 and https://th-apex-http-callout.herokuapp.com/path2.
6. For the description, enter Trailhead animal service: HTTP.
7. Click Save & New.
8. Rpeat the same for other endpoint.

![image](https://github.com/HargunaniHarsha/Customer-Relationship-Management/assets/90439153/805b6ea4-bbef-4b0f-acc3-9a6afb0bc786)


