
========================
Sphinx
========================

**********************
Documentação
**********************



Resumo RST
==========

.. code-block:: rst

  # for Parts
  * for Chapters
  = for sections (“Heading 1”)
  - for subsections (“Heading 2”)
  ^ for subsubsections (“Heading 3”)
  " for paragraphs (“Heading 4”)
  Itálico: *text*
  Negrito:  **text**
  Bloco: ``text``

note (  .. note::  )

.. note:: Este é o texto da nota. Esta parte está em  ``monospaced text``.

warning (  .. warning::  )

.. warning:: Este é o texto de warning. Esta parte está em ``monospaced text``.
  Proceed with caution!
  Proceed with caution!

Ver também (  .. seealso::  )

.. seealso::

    `Link 1 <http://pythonhosted.org/mrjob>`_
         Descrição do link

    `Link 2 <http://playbuildy.com>`_
         Descrição do link

Ver também  ( .. figure::  )

.. figure:: images/neelix.jpeg
  :width: 25%

  Neelix é um personagem principal da série americana de ficção científica Star Trek: Voyager, interpretado pelo ator Ethan Phillips.


code-block

Line numbers with the second line emphasized:

.. code-block:: python
    :linenos:
    :emphasize-lines: 2

    if True:
        print "This is some Python"

No line numbers:

.. code-block:: python

  if True:
      print "This is some Python"

Mostrar o conteudo de um arquivo:

.. literalinclude:: files/example.rb
   :language: jinja


**Tópicos**

This is example of topics

* Topic 1

  * Topic 1.1

    * Topic 1.1.1
    * Topic 1.1.2
    * Topic 1.1.3

* Topic 2
* Topic 3

.. sidebar:: Título Lateral
  :subtitle: Optional Sidebar Subtitle

  Subsequent indented lines comprise
  the body of the sidebar, and are
  interpreted as body elements.


.. topic:: Título como Tópico

  Subsequent indented lines comprise
  the body of the topic, and are
  interpreted as body elements.



Download de arquivo

:download:`download example.rb <files/example.rb>`

Tópicos com 3 colunas

.. hlist::
  :columns: 3

  * first item
  * second item
  * 3d item
  * 4th item
  * 5th item

Está é uma citação do rodapé, Some text that requires a footnote [#f1]_ .

.. rubric:: Footnotes

.. [#f1] Text of the first footnote.


Referência com link

.. _Python: http://www.python.org/

and to refer to it, use the same syntax as for the internal links: just insert the alias in the text (e.g., Python_, which appears as Python_ ).


Substituições de texto longo

A second method is as follows:

.. |longtext| replace:: this is a very very long text to include and then insert  wherever required.

texto longo |longtext|

Substituição de imagem


.. |logo| image:: images/neelix.jpeg
    :width: 20pt
    :height: 20pt

|logo|


.. todo_include_todos=True

.. |file_icon| image:: ../_static/icons/Document.png

|file_icon|  ``terraform.tfvars``: Arquivo com as credenciais da AWS (.gitignore)

.. literalinclude:: ../terraform/files/demo-2/terraform.tfvars


Instalação
============

Instalação do sphinx

.. code:: bash

   $ pip install sphinx

Instalação do Tema

.. code:: console

   Tema: https://github.com/rtfd/sphinx_rtd_theme/blob/master/README.rst
   $ pip install sphinx_rtd_theme


Editar o arquivo ``conf.py``

.. code-block:: python

   import sphinx_rtd_theme
   html_theme = "sphinx_rtd_theme"
   html_theme_path = [sphinx_rtd_theme.get_html_theme_path()]



Montar o Source
================

Editar  ``C:\Users\pepi\Documents\howto-pepi\source\index.rst``.

.. code-block:: python

  	Manuais
  	----------
  	.. toctree::
  	   :maxdepth: 1
  	   :numbered:

  	   novo_item_aqui/index

Criar subdiretório ``C:\Users\pepi\Documents\howto-pepi\source\novo_item_aqui\``

Criar Arquivo  ``C:\Users\pepi\Documents\howto-pepi\source\novo_item_aqui\index.rst``

Compilar
=============

.. code:: bash

    $ make html


**************************
LibreOffice Draw (visio)
**************************

Baixar Estencils e Ícones
===========================

Clique no link para baixar

Configurar
===========================

- clique em ``Exibir`` e depois em ``Categoria``
- clique em ``Novo Tema`` para adicionar os ícones.



**********************
Criação de Conteúdo
**********************

Edição de Vídeos
======================

:download:`dicas pdf_diolinux  <files/diolinux-e-book-10-dicas-para-editar-videos.pdf>`




kdenlive (editor de vídeo)
-------------------------------

.. code-block:: shell

    sudo apt-get install kdenlive  kdenlive-data kdenlive-dbg  breeze frei0r-plugins


kdenlivei       = editor de vídeo
breeze          = tema do kdenlive (instala o breeze dark like premier)
frei0r-pluginsi = (programa OBS ) capturar webcam e audio 

* Settings / Configure:

  * Projects defaults: 

    * Profile:  HD 1080 30fps
    * Video tracks: 3
    * Audiotracks: 3
    * Encoding: x264 é melhor que o mpeg 

  * Time preview: automatic

    * Custom project folder:




