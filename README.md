<!-- Output copied to clipboard! -->

<!-----

Yay, no errors, warnings, or alerts!

Conversion time: 0.354 seconds.


Using this Markdown file:

1. Paste this output into your source file.
2. See the notes and action items below regarding this conversion run.
3. Check the rendered output (headings, lists, code blocks, tables) for proper
   formatting and use a linkchecker before you publish this page.

Conversion notes:

* Docs to Markdown version 1.0β33
* Wed Sep 28 2022 16:57:28 GMT-0700 (PDT)
* Source doc: Angular with Java Services Free Online
----->



# Angular with Java Services Free Online


## AFK Story

I had created [REST Web Services](https://spring.io/guides/gs/rest-service) on [OpenShift](https://developers.redhat.com/developer-sandbox) using [Spring Boot](https://start.spring.io/) [Java](https://www.java.com) [JPA](https://spring.io/projects/spring-data-jpa) [MariaDB](https://mariadb.org)([MySQL](https://www.mysql.com)), and they were tested and deployed. OpenShift allows many types of deployments, including Node, but I couldn't figure out how to deploy an [Angular](https://angular.io) site on OpenShift, so I decided to deploy my Angular website on [Firebase](https://console.firebase.google.com). After struggling with deploying to bth sites for a a month, I had gotten the site running with just an error when calling the wrong REST endpoint. I fixed the endpoint and had no errors, when my son was pulling me [AFK](https://en.wikipedia.org/wiki/AFK) to go to [McDonalds](https://www.mcdonalds.com). I wanted to figure out this problem, but I could only do it while AFK. I had known that the Angular site worked, the REST services worked, but the data wasn't showing up on the Angular web page. By the time I arrived at McDonalds, I had already narrowed the problem down to a [HTML](https://www.w3schools.com/html) View issue. I knew this because of the [MVC](https://en.wikipedia.org/wiki/Model%E2%80%93view%E2%80%93controller) paradigm: if the Model was broken between the Angular site and the REST services, then I would have seen an error; if the controller wasn't working, then I wouldn't have seen REST errors previously, so it had to be a data-to-HTML issue, which was quickly fixed when I returned home.

I had originally started with [CloudBees](https://www.cloudbees.com) when it was free, then migrated to [Heroku](https://www.heroku.com) which recently became unfree, and wanted to switch to OpenShift but had to also switch to FireBase for Angular programming.  Firebase does not host free Java websites.

I tried [000webhost](https://www.000webhost.com), which also didn't host Java websites for free.

I have programmed for over 40 years, started with Java 1.0, and recently learned Angular on the job. So I knew how to setup Angular-to-JavaREST website, but not how to host it on OpenShift or FireBase, so I went about [Google](https://www.google.com)-ing for examples of how to deploy.

There's _tons_ of IBM RedHat OpenShift and Google FireBase documentation and user sites on [GitHub](https://github.com) and elsewhere online.

After a month I figured out how to **deploy to OpenShift without any programming or YAML, JSON or Docker files**, mostly by using [this site](https://medium.com/fnplus/deploying-your-first-springboot-application-on-openshift-1dd5833aaab9).



* I created a project with a MariaDB by going to [OpenShift site](https://console-openshift-console.apps.sandbox.x8i5.p1.openshiftapps.com/catalog/ns/ftaylor92-dev?category=databases&keyword=maria), selecting +Add, selecting Database, and then selecting MariaDB
* Then I created the initial Spring-boot JPA MariaDB web services site without coding using [Spring Initializer](https://start.spring.io)
* (necessary only if using database) Then I changed spring.datasource.url, spring.datasource.username and spring.datasource.password in application.properties file in the downloaded code from Spring Initializer, and added my bookstore-specific code for REST endpoints.
* (unnecessary) I tested my code locally with mvn package spring-boot:run with a locally installed MariaDB
* (unnecessary) I also tested my OpenShift with a local installation of MiniShift, but MiniShift is v3 and OpenShift is v4.11 currently
* I pushed this code to a GitHub [repo](https://github.com/ftaylor92/springboot-webservice-simplest)
* Then I imported my GitHub repo into OpenShift by selecting +Add -> Import from Git -> https://github.com/ftaylor92/springboot-webservice-simplest -> (and these setting allow my website and webservices to be served via HTTPS, not HTTP) -> Show Advanced Routing Options -> TLS Termination: Edge, Insecure Traffic: None
* Then the site was up and running!
    * curl -i -X GET [https://springboot-webservice-simplest-git-ftaylor92-dev.apps.sandbox.x8i5.p1.openshiftapps.com/books](https://springboot-webservice-simplest-git-ftaylor92-dev.apps.sandbox.x8i5.p1.openshiftapps.com/books)
    * [https://springboot-webservice-simplest-git-ftaylor92-dev.apps.sandbox.x8i5.p1.openshiftapps.com/books](https://springboot-webservice-simplest-git-ftaylor92-dev.apps.sandbox.x8i5.p1.openshiftapps.com/books)

Spoiler alert: I had to deploy webservices to HTTPS because HTTP didnt work with Angular site on FireBase.

Then I had to **create and deploy my Angular site **to display data from my REST services

I started with [this code](https://github.com/FirebaseExtended/codelab-kanban-fire/tree/improving-optimistic-updates), and then added HTML, Services and Component code and pushed it to a GitHub [repo](https://github.com/ftaylor92/angular-rest-firebase) (not node-modules/ folder or package-lock.json file), and followed the rest of the [tutorial](https://developers.google.com/codelabs/building-a-web-app-with-angular-and-firebase#9) to deploy my [webapp](https://kanbanfire-5712f.web.app).

There's still issues, like OpenShift Pods going to sleep and Angular sending OPTION instead of GET, but I feel good to have gotten this far.

My email is [fmtaylor92@gmail.com](mailto:fmtaylor92@gmail.com) is you have suggestions or need help, and my site is [http://fmt-drive.herokuapp.com/public-web-site/index.html](http://fmt-drive.herokuapp.com/public-web-site/index.html), which will change when Heroku finally goes down.
