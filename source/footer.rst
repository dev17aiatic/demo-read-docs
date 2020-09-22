COMPONENTE FOOTER
=================

El componente de footer está creado con el fin de mostrarse al final de nuestra página web y este debe mostrarse en todas las páginas que componen el aplicativo.


.. code-block::

      <!-- Footer -->
      <footer>

            <div class="footer">© 2020 Copyright:
              <a href="https://aiatic.com"> A&A SOLUCIONES TIC</a>
            </div>

      </footer>

reglas definidas en nuestro scss para el estilo de nuestro footer.

.. code-block::
 
      .footer {
        z-index: 1;
        position: relative;
        left: 0;
        bottom: 0;
        margin: auto;
        margin-top: 0;
        margin-bottom: 0;
        width: 100%;
        background-color: rgb(255, 136, 0);
        color: white;
        text-align: center;
      }

