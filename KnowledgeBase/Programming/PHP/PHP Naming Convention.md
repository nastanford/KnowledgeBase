# PHP Naming Convention
#phpnamingconvention #php 


* Table - plural - article_comments
* Table Column - meta_title
* Primary Key - id
* Foreign Key - article_comments_id
* XREF Table - article_comments_people
* Bean - People - single instance of a people
  * getPersonBy(id)
  * get"property"/set"property" - getFirstName/setFirstName
  * create object abc  abc.setFirstName($_POST.firstName);
* userBean - single user
* userDao - crud of single user
* userGateway - Get All Users etc
