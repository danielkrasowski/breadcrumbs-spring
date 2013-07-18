## BreadCrumbs for Spring MVC

<i>breadcrumbs-spring.jar</i> is library dedicated for Spring MVC. This library based on annotation and interceptor. Additionally annotation includes few attributes, which allow for some customization:

<b>Label</b> - Display label for the link. You can define static text or key of element at property file.<br>
<b>Parent</b> – define parent of current localization. Parent with empty value indicate that it is root of user position.<br>
<b>Message</b> - Attribute allow only Boolean type and it indicate that definition of bread crumbs based on message properties, including right localization.<br>
<b>Dynamic</b> – Attribute allow only Boolean type and it indicate that, the label can be sat dynamically from method. Only what you mas too do, use instance of <i>Model</i> and label by <i>model.addAttribute(“breadLabel”, “Welcome”);</i><br>

## Examples

<b>Example 1:</b>
Static text of label
```java
@Bread(label="Welcome", parent="")
@RequestMapping(value="/page", method=RequestMethod.GET)
public String getCandidate(Model model) {
  	return "page";
}
```

<b>Example 2:</b>
Label loaded from message properties file
```java
@Bread(label="welcome.editTitle", parent="w1", message=true)
@RequestMapping(value="/page", method=RequestMethod.GET)
public String getCandidate(Model model) {
	return "page";
}
```

<b>Example 3:</b>
Dynamic settings of label
```java
@Bread(parent="w2", dynamic=true)
@RequestMapping(value="/page", method=RequestMethod.GET)
public String getCandidate(Model model) {
	model.addAttribute("breadLabel", "Welcome");	
	return "page";
}
```

## Installation

1. Paste breadcrumbs-spring.jar to lib directory at WEB-INF
2. At Spring config descriptor, define interceptor

```xml
	<mvc:annotation-driven/>
	<context:annotation-config />
	
	<mvc:interceptors>
		<mvc:interceptor>
			<mvc:mapping path="/**" />
			<ref bean="breadInterceptor"/>
		</mvc:interceptor>
	</mvc:interceptors>
	
	<bean id="breadInterceptor" class="springmvc.dataframe.breadcrumbs.BreadInterceptor">
		<property name="messageSource" ref="messageSource" />
	</bean>
```

3. At your controller, add annotation to method e.g. <i>@Bread(label="Welcome", parent="")</i>
4. Add view element 

```html

	<ul class="breadcrumb">
		<c:forEach var="item" items="${sessionScope.breadcrumbs}">
			<c:choose>
				<c:when test="${item.currentPage == true}">
					 <li class="active">${item.label}</li>
				</c:when>
				<c:otherwise>
					<li><a href="${item.url}">${item.label}</a> <span class="divider">/</span></li>
				</c:otherwise>
			</c:choose>
		</c:forEach>
	</ul>
```
