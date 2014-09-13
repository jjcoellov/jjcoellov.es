---
layout: post
status: publish
published: true
title: 'Test Técnico de Java '
author:
  display_name: Juanjo
  login: juanjo
  email: juanjo@jjcoellov.es
  url: http://www.jjcoellov.es
author_login: juanjo
author_email: juanjo@jjcoellov.es
author_url: http://www.jjcoellov.es
wordpress_id: 47
wordpress_url: http://jjcoellov.es/?p=47
date: '2009-02-02 15:50:11 +0000'
date_gmt: '2009-02-02 14:50:11 +0000'
categories:
- Coding
- Informática
tags:
- java coding programacion
---
<p>No me acuerdo exactamente donde fue que encontré las siguientes preguntas, pero si son verídicas, soy un completo <strong>ignorante</strong> (por cierto, no es lo mismo <em>intuirlo</em> que <em>corroborarlo</em>). Al parecer, son preguntas que se hacen en la parte "técnica" de las entrevistas de trabajo para ingenieros informáticos en el Reino Unido. Son bastante bastante concretas sobre Java... y no sé ni una. Creo que me queda <strong>mucho</strong > que estudiar para aspirar a las certificaciones Sun...</p>
<p>Aquí van las preguntas (en inglés):</p>
<p><strong>1- Troubleshoot the following class that is producing performance errors on the site:</strong></p>
<pre lang="Java" line="1">
package com.blah.dataaccess;  

import java.sql.*; 
import javax.sql.*;  
import com.blah.data.*;  

public class GetFormats {   	

   private Connection con;  	

   public static String GetFormat(String user) 	{ 	 		
      String format = "mpeg4_150k";
      try {
         con = ConnectionFactory.getConnection();
         String sql_string = "select wfmt_urlroot from wprf, wfmt where wprf_value = wfmt_id and wprf_type = 'bandwidth' and wprf_wusr_id = ?";
         PreparedStatement pstmt = con.prepareStatement(sql_string);
         pstmt.setString(1, user);
         ResultSet rs = pstmt.executeQuery();
         if (rs != null) {
            while (rs.next()) { 
               format = rs.getString(1);
            }
         }
      } catch (SQLException e) {
          String error = ""+ e.toString();
      }
      return formats;
      }
   }
}
</pre>
<p><strong>2- What’s wrong with the following Tag:</strong></p>
<pre lang="Java" line="1">
package com.blah.webui;  

import java.sql.*; 
import java.lang.*; 
import java.util.*; 
import java.net.URLEncoder;  

public class OutputFooter extends TagSupport {
   
   public String Footer() {
      String html = "";
      html = html + "</body></html>";
      return html;
   }
   
   public int doStartTag() throws JspException {
      try {
         // and write out the formatted content to the page
         pageContext.getOut().write(Footer());
      } catch (java.io.IOException ioe) {
         throw new JspTagException(ioe.getMessage());
      }
      // and skip evaluating the body of the tag (as there shouldn't be one)
      return SKIP_PAGE;     
   }
}
</pre>
<p><strong>3- If you need to obtain and return the referring URL into a JSP page, how would you do it? </strong></p>
<p><strong>4- Describe how you would set up servlet mappings in Tomcat or any other J2EE servlet container, what would you do to involve Apache in this process to provide a unified URL convention for static and dynamic elements of the site.</strong></p>
<p><strong>5- Describe the steps involved in making Apache and a servlet container such as Tomcat work together. Discuss the relative merits of mod_jk and mod_proxy.</strong></p>
<p><strong>6- Discuss the differences between redirection and forwarding in the Java server environment within a cluster, between servers in a cluster and between sites.</strong></p>
<p><strong>7- Describe how serving of static and dynamic fragments can best be done in a clustered environment for high efficiency under high load with maximum availability.</strong></p>
<p><strong>8- The company has decided to settle on memcached to provide a distributed cache store. Describe how you would create a set of custom tags to provide an interface to memcached to provide for creating, updating, invalidating and retrieving cached items.</strong></p>
<p><strong>9- Explain the steps, giving references to libraries you would use, to enable elements from a content management system to connect with XML-RPC services to provide pings.</strong></p>
<p><strong>10- What's your preferred way of parsing incoming XML and why?</strong></p>
<p><strong>11- Describe the stages involved in getting Ant, subversion and Eclipse working together to automatically build a tree from a subversion repository and deploy it to Tomcat.</strong></p>
<p><strong>12- Discuss the relative merits of
<pre lang="HTML"><c:import></pre>
<p> and
<pre lang="HTML"><jsp:include></pre>
<p></strong></p>
<p><strong>13- Discuss the difference between a custom tag which supports EL and one which supports RT.</strong></p>
<p><strong>14- Describe (with code examples if possible) how you would use an EL based JSP fragment to iterate through a simple XML file and make decisions based on the values of certain nodes.</strong></p>
<p><strong>15- The introduction of JSR-220 brought with it JPA. Hibernate is an open source ORM solution. Briefly describe, with a small example if possible, the impact JPA has had on the Hibernate project, and what steps would need to be taken to convert an existing hibernate project to conform with the JPA specification in JSR-220. What advantages to would this conversion bring?</strong></p>
<p><strong>16- When using a persistence layer within a multi-threaded environment which has the potential for a long object lifetime, special precautions must be made to ensure the system can maintain a high degree of concurrency, and also work correctly in a clustered environment. Give a short explanation of the problem domain and a potential high-level solution.</strong></p>
<p><strong>17- Explain the following method signature: </strong></p>
<pre lang="Java">
<T extends Myobject> T getMyobject(Class<T> MyObjectType);
</pre>
<p><strong>18- Explain the difference between phantom, soft, strong and weak references and  give a context they would be used in.</strong></p>
<p><strong>19-Diagnose the following exception, found in the tomcat catalina.out file:</strong></p>
<pre lang="text">
java.security.AccessControlException: access denied (java.net.SocketPermission 192.168.1.244:80 connect,resolve) 
	at java.security.AccessControlContext.checkPermission(AccessControlContext.java:264) 	
        at java.security.AccessController.checkPermission(AccessController.java:427) 	
        at java.lang.SecurityManager.checkPermission(SecurityManager.java:532)
 	at java.lang.SecurityManager.checkConnect(SecurityManager.java:1034)
 	at sun.net.www.http.HttpClient.openServer(HttpClient.java:459)
 	at sun.net.www.http.HttpClient.<init>(HttpClient.java:214)
 	at sun.net.www.http.HttpClient.New(HttpClient.java:287)
 	at sun.net.www.http.HttpClient.New(HttpClient.java:299)
 	at sun.net.www.protocol.http.HttpURLConnection.getNewHttpClient(HttpURLConnection.java:796)
 	at sun.net.www.protocol.http.HttpURLConnection.plainConnect(HttpURLConnection.java:748)
 	at sun.net.www.protocol.http.HttpURLConnection.connect(HttpURLConnection.java:673)
 	at sun.net.www.protocol.http.HttpURLConnection.getInputStream(HttpURLConnection.java:917)
 	at org.apache.taglibs.standard.tag.common.core.ImportSupport.acquireReader(ImportSupport.java:331) 
....... 
</pre>
<p><strong>20- Design a simple three database table structure which would allow the creation, editing and publication of a webpage stored in a content management system. </strong></p>
<p>Concurrencia, clústering, parsing XML, diseño DB, Templates..... En pocas palabras, <strong>la-le-che</strong> :P</p>
