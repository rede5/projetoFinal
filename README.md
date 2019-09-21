<h1>Seção 4: Desenvolvendo uma aplicação real</h1>

<h2>21. Criação do projeto e versionando a aplicaçãocom GIT</h2>

<p>Criação Virtualenv</p>

<ul>
<li>python3 -m venv pf-venv</li>
</ul>

<p>Ativação Virtualenv</p>

<ul>
<li>. pf-venv/bin/activate</li>
</ul>

<p>Instalação Django</p>

<ul>
<li>pip install django</li>
</ul>

<p>Criação do Projeto</p>

<ul>
<li>django-admin startproject gestao_clientes</li>
</ul>

<h2>22. Migração da App Clientes</h2>

<p>Renomeação da pasta meus_templates e copiada para dentro da pasta clientes, 
depois copiada para dentro da pasta gestao_clientes/gestao_cliente</p>

<h2>23. Habilitando o login para alterações de cadastros</h2>

<p>projetoFinal/gestao_clientes/clientes/views.py</p>

```python
from django.contrib.auth.decorators import login_required
@login_required
```` 
<p>projetoFinal/gestao_clientes/gestao_clientes/urls.py</p>

```python
from django.contrib.auth import views as auth_views

path('login/', auth_views.LoginView.as_view(), name='login'),
path('logout/', auth_views.LogoutView.as_view(), name='logout'),
````

<p>projetoFinal/gestao_clientes/gestao_clientes/settings.py</p>

```python
LOGIN_URL = '/login/'

LOGIN_REDIRECT_URL = 'person_list'
````  

<p>projetoFinal/gestao_clientes/templates/registration/login.html</p>
<p>Criar a pasta registration em templates</p>   

```html
<h2>Login</h2>
<form method="post">
      {% csrf_token %}
      {{ form.as_p }}
<button type="submit">Login</button>
</form>
````
<p>projetoFinal/gestao_clientes/clientes/templates/person.html</p>

```html
<a href="{% url 'logout' %}">Sair</a>
```` 