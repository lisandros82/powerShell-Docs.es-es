# <a name="powershell-core-support-lifecycle"></a>Ciclo de vida de soporte técnico de PowerShell Core

PowerShell Core es un conjunto independiente de herramientas y componentes que se entrega, se instala y se configura por separado de Windows PowerShell.
Por lo tanto, PowerShell Core no se incluye en los contratos de licencias de Windows 7/8.1/10 o Windows Server.

Sin embargo, PowerShell Core se admite en los contratos de soporte técnico convencionales de Microsoft, incluido el soporte técnico [Premier][], los [contratos Enterprise de Microsoft][enterprise-agreement] y [Microsoft Software Assurance][assurance].
También existe la opción de pagar para obtener [soporte técnico asistido][] para PowerShell Core. Basta con enviar una solicitud de soporte técnico para su problema.

También ofrecemos [soporte técnico de la comunidad][] en GitHub, donde puede registrar un problema o un error, o solicitar una característica.
Como alternativa, puede obtener ayuda de otros miembros de la comunidad en [Microsoft Community][] en general o en [PowerShell Tech Community][] de Microsoft.
No se ofrece ninguna garantía de que su problema se aborde o se resuelva oportunamente.
Si tiene algún problema que requiera atención inmediata, deberá usar las opciones convencionales de soporte técnico de pago.

## <a name="lifecycle-of-powershell-core"></a>Ciclo de vida de PowerShell Core

PowerShell Core ha adoptado la [directiva moderna de ciclo de vida de Microsoft][modern].
Este ciclo de vida de soporte técnico está diseñado para mantener a los clientes actualizados con las versiones más recientes.

La rama de la versión 6.x de PowerShell Core se actualizará aproximadamente una vez cada seis meses (por ejemplo, 6.0, 6.1, 6.2, etc.).

> [!IMPORTANT]
> Debe realizar la actualización en los seis meses siguientes al lanzamiento de cada nueva versión secundaria para seguir recibiendo soporte técnico.

Por ejemplo, si PowerShell Core 6.1 se lanza el 1 de julio de 2018, deberá actualizar a PowerShell Core 6.1 antes del 1 de enero de 2019 para conservar el soporte técnico.

![Ciclo de vida de rama de PowerShell Core][lifecycle-chart]

La directiva moderna de ciclo de vida también requiere que Microsoft avise a los clientes con 12 meses de antelación antes de interrumpir el soporte técnico para un producto (es decir, PowerShell Core).

Esperamos que, a la larga, PowerShell Core adopte un enfoque de mantenimiento a largo plazo, que solo requeriría el mantenimiento y las actualizaciones de seguridad para conservar el soporte técnico de una rama o versión específica de 6.x.

## <a name="supported-platforms"></a>Plataformas admitidas

Consulte la tabla siguiente para ver la plataforma en la que la versión de PowerShell Core que está utilizando es compatible oficialmente.

Nuestra comunidad también ha aportado paquetes para algunas plataformas, pero no se admiten oficialmente.
Estos paquetes se marcan como `Community` en la tabla.

Las plataformas mencionadas como `Experimental` no se admiten oficialmente, pero están disponibles para experimentación y comentarios.

|                                                   | 6.0         | 6.1         |
|---------------------------------------------------|:-----------:|:-----------:|
| Windows 7, 8.1 y 10                            | Compatible   | Compatible   |
| Windows Server 2008 R2, 2012 R2 y 2016             | Compatible   | Compatible   |
| [Canal semianual de Windows Server][semi-annual] | Compatible   | Compatible   |
| Ubuntu 14.04 y 16.04                           | Compatible   | Compatible   |
| Ubuntu 17.10 y 18.04                           |             | Compatible   |
| Debian 8.7+ y 9                                | Compatible   | Compatible   |
| CentOS 7                                          | Compatible   | Compatible   |
| Red Hat Enterprise Linux 7                        | Compatible   | Compatible   |
| OpenSUSE 42.2                                     | Compatible   | Compatible   |
| Fedora 27                                         | Compatible   | Compatible   |
| Fedora 28                                         |             | Compatible   |
| macOS 10.12+                                      | Compatible   | Compatible   |
| Arch                                              | Comunidad   | Comunidad   |
| Raspbian                                          | Experimental| Comunidad   |
| Kali                                              | Comunidad   | Comunidad   |
| AppImage (funciona en varias plataformas Linux)     | Comunidad   | Comunidad   |

## <a name="platform-which-are-out-of-support"></a>Plataforma que está fuera de soporte técnico

Cuando una versión de la plataforma llega al final de su vida útil definida por el propietario de la plataforma, PowerShell Core también dejará de ofrecer soporte técnico para esa versión de la plataforma. Los paquetes previamente publicados seguirán estando disponibles para los clientes que necesiten acceso, pero ya no se proporcionará soporte técnico formal ni actualizaciones de ningún tipo.

Por lo tanto, los propietarios de distribución han finalizado la compatibilidad para las versiones siguientes y ya no se admiten.

| Sistema operativo       | Version | Fin de la vida útil                                                                                 |
|----------|---------|---------------------------------------------------------------------------------------------|
| Fedora   | 26      | [Mayo de 2018](https://fedoramagazine.org/fedora-26-end-life/)                                  |
| Fedora   | 25      | [Diciembre de 2017](https://fedoramagazine.org/fedora-25-end-life/)                             |
| Fedora   | 24      | [Agosto de 2017](https://fedoramagazine.org/fedora-24-eol/)                                    |
| openSUSE | 42.2    | [Enero de 2018](https://lists.opensuse.org/opensuse-security-announce/2017-11/msg00066.html) |
| openSUSE | 42.1    | [Mayo de 2017](https://lists.opensuse.org/opensuse-security-announce/2017-05/msg00053.html)     |
| Ubuntu   | 17.04   | [Enero de 2018](https://lists.ubuntu.com/archives/ubuntu-announce/2018-January.txt)          |
| Ubuntu   | 16.10   | [Julio de 2017](https://lists.ubuntu.com/archives/ubuntu-announce/2017-July/000223.html)        |

## <a name="notes-on-licensing"></a>Notas sobre las licencias

PowerShell Core se publica bajo la [licencia de MIT][].
De acuerdo con esta licencia, y en ausencia de un contrato de soporte técnico de pago, los usuarios están limitados al [soporte técnico de la comunidad][].
Con el soporte técnico de la comunidad, Microsoft no garantiza la capacidad de respuesta ni correcciones para el usuario.

## <a name="windows-powershell-module"></a>Módulo de Windows PowerShell

El soporte técnico para PowerShell Core no se extiende a otros módulos de producto, a menos que dichos módulos admitan explícitamente PowerShell Core.
Por ejemplo, el uso del módulo `ActiveDirectory` que se suministra como parte de Windows Server es un escenario que no se admite.

Sin embargo, los módulos que no admiten explícitamente PowerShell Core podrían ser compatibles en algunos casos.
Si instala el módulo [`WindowsPSModulePath`][] puede agregar `PSModulePath` de Windows PowerShell a `PSModulePath` de PowerShell Core.

En primer lugar, instale el módulo `WindowsPSModulePath` desde la Galería de PowerShell:

```powershell
# Add `-Scope CurrentUser` if you're installing as non-admin
Install-Module WindowsPSModulePath -Force
```

Después de instalar este módulo, ejecute el cmdlet `Add-WindowsPSModulePath` para agregar `PSModulePath` de Windows PowerShell a PowerShell Core:

```powershell
# Add this line to your profile if you always want Windows PowerShell PSModulePath
Add-WindowsPSModulePath
```

[Premier]: https://www.microsoft.com/en-us/microsoftservices/support.aspx
[enterprise-agreement]: https://www.microsoft.com/en-us/licensing/licensing-programs/enterprise.aspx
[assurance]: https://www.microsoft.com/en-us/licensing/licensing-programs/software-assurance-default.aspx
[Soporte técnico de la comunidad]: https://github.com/powershell/powershell/issues
[Microsoft Community]: https://answers.microsoft.com/
[PowerShell Tech Community]: https://techcommunity.microsoft.com/t5/PowerShell/ct-p/WindowsPowerShell
[Soporte técnico asistido]: https://support.microsoft.com/assistedsupportproducts
[modern]: https://support.microsoft.com/help/30881/modern-lifecycle-policy
[lifecycle-chart]: ./images/modern-lifecycle.png
[semi-annual]: https://docs.microsoft.com/windows-server/get-started/semi-annual-channel-overview
[Licencia de MIT]: https://github.com/PowerShell/PowerShell/blob/master/LICENSE.txt
["WindowsPSModulePath"]: https://www.powershellgallery.com/packages/WindowsPSModulePath/
