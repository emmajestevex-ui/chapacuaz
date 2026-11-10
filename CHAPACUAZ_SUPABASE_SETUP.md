# CHAPACUAZ IOS — Supabase

1. Abre el SQL Editor del proyecto nuevo.
2. Pega y ejecuta `supabase/CHAPACUAZ_SETUP_ALL.sql` completo, una sola vez.
3. En Authentication > Users crea o confirma el usuario administrador usando uno de los correos incluidos en el SQL.
4. Abre `admin/start-panel.cmd`, entra con ese usuario y publica un archivo de prueba.
5. Verifica que el manifiesto se publique y luego sincroniza la app.

El cliente iOS y el panel usan únicamente la clave publishable. Nunca pongas una `service_role` o una clave secreta en la IPA, el panel web o el bot.

El bot necesita además estas variables en el entorno donde se ejecuta:

```text
CHAPACUAZ_ADMIN_EMAIL=correo-del-usuario-admin
CHAPACUAZ_ADMIN_PASSWORD=contrasena-del-usuario-admin
```

Después de reiniciar el bot, ejecuta `/preparar-canales` en el servidor configurado para crear o actualizar el rol `KEYS CHAPACUAZHACKS` y el canal `keys-chapacuazhack`.
