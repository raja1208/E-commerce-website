{% extends 'shop/base.html' %}
{% load static %}
{% block title %}
Your Shopping Cart
{% endblock %}


{% block content %}
&lt;div class="container"&gt;
&lt;div class="row" style="margin-top: 6%"&gt;
&lt;h2&gt;Your Shopping Cart
&lt;span class="badge pull-right"&gt;
{% with totail_items=cart|length %}
{% if cart|length &gt; 0 %}
My Shopping Order:
&lt;a href="{% url "cart:cart_detail" %}" style="color: green"&gt;
{{ totail_items }} item {{ totail_items|pluralize }}, P{{ cart.get_total_price }}
&lt;/a&gt;
{% else %}
Your cart is empty.
{% endif %}
{% endwith %}
&lt;/span&gt;
&lt;/h2&gt;
&lt;table class="table table-striped table-hover"&gt;
&lt;thead style="background-color: navajowhite"&gt;
&lt;tr&gt;
&lt;th&gt;Image&lt;/th&gt;
&lt;th&gt;Product&lt;/th&gt;
&lt;th&gt;Quantity&lt;/th&gt;
&lt;th&gt;Remove&lt;/th&gt;
&lt;th&gt;Unit Price&lt;/th&gt;
&lt;th&gt;Price&lt;/th&gt;
&lt;/tr&gt;
&lt;/thead&gt;
&lt;tbody&gt;
{% for item in cart %}
{% with product=item.product %}
&lt;tr&gt;
&lt;td&gt;
&lt;a href="{{ product.get__absolute_url }}"&gt;
&lt;img src="{% if product.image %} {{ product.image.url }} {% else %} {% static 'img/default.jpg' %} {% endif %}" alt="..." style="height: 130px; width: auto"&gt;
&lt;/a&gt;
&lt;/td&gt;
&lt;td&gt;{{ product.name }}&lt;/td&gt;
&lt;td&gt;
&lt;form action="{% url "cart:cart_add" product.id %}" method="post"&gt;
{% csrf_token %}
{{ item.update_quantity_form.quantity }}
{{ item.update_quantity_form.update }}
&lt;input type="submit" value="Update" class="btn btn-warning" &gt;
&lt;/form&gt;
&lt;/td&gt;
&lt;td&gt;
&lt;a style="color: red" href="{% url "cart:cart_remove" product.id %}"&gt;Remove&lt;/a&gt;
&lt;/td&gt;
&lt;td&gt;P{{ item.price }}&lt;/td&gt;
&lt;td&gt;P{{ item.total_price }}&lt;/td&gt;
&lt;/tr&gt;
{% endwith %}
{% endfor %}
&lt;tr style="background-color: navajowhite"&gt;
&lt;td&gt;&lt;b&gt;Total&lt;/b&gt;&lt;/td&gt;
&lt;td colspan="4"&gt;&lt;/td&gt;
&lt;td colspan="num"&gt;&lt;b&gt;P{{ cart.get_total_price }}&lt;/b&gt;&lt;/td&gt;
&lt;/tr&gt;
&lt;/tbody&gt;
&lt;/table&gt;
&lt;p class="text-right"&gt;
&lt;a href="{% url "shop:product_list" %}" class="btn btn-default"&gt;Continue Shopping&lt;/a&gt;
&lt;a href="{% url "orders:order_create" %}" class="btn btn-warning"&gt;Checkout&lt;/a&gt;
&lt;/p&gt;
&lt;/div&gt;
&lt;/div&gt;
{% endblock %}
