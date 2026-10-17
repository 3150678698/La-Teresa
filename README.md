

<!DOCTYPE html>

<html lang="es">

<head>

  <meta charset="UTF-8">

  <meta name="viewport" content="width=device-width, initial-scale=1.0">

  <meta name="theme-color" content="#000000">

  <title>LA TERESA | Administración Rural</title>

  <style>

    * { box-sizing: border-box; }

    body {

      margin: 0;

      background: #f4f4f4;

      color: #111;

      font-family: -apple-system, BlinkMacSystemFont, Arial, sans-serif;

    }

    header {

      background: #000;

      color: #fff;

      padding: 28px 20px;

    }

    .marca { font-size: 12px; letter-spacing: 4px; }

    header h1 { font-size: 32px; margin: 12px 0 5px; }

    header p { color: #ccc; font-size: 14px; margin: 0; }

    main { padding: 20px; max-width: 700px; margin: auto; }

    .fecha { color: #666; font-size: 12px; margin-bottom: 20px; }

    .resumen {

      background: #fff; border: 1px solid #ddd;

      padding: 18px; margin-bottom: 24px;

    }

    .resumen small { color: #666; }

    .resumen h2 { margin: 8px 0; font-size: 21px; }

    h3 { font-size: 15px; margin: 24px 0 12px; }

    .modulos {

      display: grid; grid-template-columns: 1fr 1fr; gap: 12px;

    }

    .modulo {

      display: block; text-align: left; width: 100%;

      padding: 17px 14px; min-height: 115px;

      background: white; color: #111;

      border: 1px solid #ddd; border-radius: 4px;

      font: inherit; cursor: pointer;

    }

    .modulo:active { background: #e5e5e5; }

    .simbolo { font-size: 23px; display: block; margin-bottom: 12px; }

    .modulo strong { display: block; font-size: 14px; }

    .modulo small { display: block; color: #666; margin-top: 6px; }

    .panel {

      display: none; background: #fff; border: 1px solid #ddd;

      padding: 20px; margin-top: 20px;

    }

    .panel.activo { display: block; }

    .volver {

      background: #000; color: white; border: 0;

      padding: 12px 18px; margin-top: 16px; cursor: pointer;

    }

    footer { text-align: center; padding: 28px 10px; color: #777; font-size: 11px; }

    @media (max-width: 360px) {

      .modulos { grid-template-columns: 1fr; }

    }

  </style>

</head>

<body>

  <header>

    <div class="marca">GESTIÓN AGROPECUARIA</div>

    <h1>LA TERESA</h1>

    <p>Administración inteligente del campo.</p>

  </header>

  <main>

    <div class="fecha" id="fecha"></div>

    <section class="resumen">

      <small>PANEL PRINCIPAL</small>

      <h2>Bienvenida a La Teresa</h2>

      <p>Organiza las actividades, los animales y los recursos de la finca desde un solo lugar.</p>

    </section>

    <h3>MÓDULOS DE LA FINCA</h3>

    <div class="modulos">

      <button class="modulo" onclick="abrir('porcinos')">

        <span class="simbolo">01</span>

        <strong>Porcicultura</strong>

        <small>Cerdas, partos y engorde</small>

      </button>

      <button class="modulo" onclick="abrir('ganaderia')">

        <span class="simbolo">02</span>

        <strong>Ganadería</strong>

        <small>Bovinos y producción</small>

      </button>

      <button class="modulo" onclick="abrir('aves')">

        <span class="simbolo">03</span>

        <strong>Avicultura</strong>

        <small>Gallinas y producción</small>

      </button>

      <button class="modulo" onclick="abrir('peces')">

        <span class="simbolo">04</span>

        <strong>Piscicultura</strong>

        <small>Peces y estanques</small>

      </button>

      <button class="modulo" onclick="abrir('inventario')">

        <span class="simbolo">05</span>

        <strong>Inventario</strong>

        <small>Alimentos e insumos</small>

      </button>

      <button class="modulo" onclick="abrir('finanzas')">

        <span class="simbolo">06</span>

        <strong>Finanzas</strong>

        <small>Gastos e ingresos</small>

      </button>

      <button class="modulo" onclick="abrir('actividades')">

        <span class="simbolo">07</span>

        <strong>Actividades</strong>

        <small>Tareas y seguimiento</small>

      </button>

      <button class="modulo" onclick="abrir('reportes')">

        <span class="simbolo">08</span>

        <strong>Reportes</strong>

        <small>Resumen de la finca</small>

      </button>

    </div>

    <section id="panel" class="panel">

      <small id="numero"></small>

      <h2 id="titulo"></h2>

      <p id="descripcion"></p>

      <p>Este módulo está preparado para que agreguemos sus formularios y registros.</p>

      <button class="volver" onclick="cerrar()">Volver al menú</button>

    </section>

  </main>

  <footer>LA TERESA · SISTEMA DE ADMINISTRACIÓN RURAL</footer>

  <script>

    document.getElementById('fecha').textContent =

      new Intl.DateTimeFormat('es-CO', {

        dateStyle: 'long'

      }).format(new Date());

    const modulos = {

      porcinos: ['01', 'Porcicultura', 'Gestiona las cerdas, inseminaciones, gestaciones, partos, lechones, alimentación, medicamentos y etapas de engorde.'],

      ganaderia: ['02', 'Ganadería', 'Organiza el inventario bovino, nacimientos, reproducción, salud y producción.'],

      aves: ['03', 'Avicultura', 'Controla las gallinas, producción de huevos, alimentación y novedades.'],

      peces: ['04', 'Piscicultura', 'Registra estanques, población de peces, alimentación, mortalidad y cosechas.'],

      inventario: ['05', 'Inventario', 'Administra concentrado, medicamentos, materiales y existencias.'],

      finanzas: ['06', 'Finanzas', 'Organiza los ingresos, gastos, compras y costos de producción.'],

      actividades: ['07', 'Actividades', 'Planifica las labores diarias y registra las actividades realizadas.'],

      reportes: ['08', 'Reportes', 'Prepara resúmenes de producción, inventario y resultados económicos.']

    };

    function abrir(id) {

      const m = modulos[id];

      document.getElementById('numero').textContent = 'MÓDULO ' + m[0];

      document.getElementById('titulo').textContent = m[1];

      document.getElementById('descripcion').textContent = m[2];

      document.getElementById('panel').classList.add('activo');

      document.getElementById('panel').scrollIntoView({behavior:'smooth'});

    }

    function cerrar() {

      document.getElementById('panel').classList.remove('activo');

      window.scrollTo({top:0, behavior:'smooth'});

    }

  </script>

</body>

</html>