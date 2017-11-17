---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: d3a625d05eaf4e7448b4abf90499f6a94e2f7718
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/12/2017
---
# <a name="allowing-for-identical-duplicate-resources-in-a-configuration"></a><span data-ttu-id="a8c2d-102">Permitir recursos duplicados idénticos en una configuración</span><span class="sxs-lookup"><span data-stu-id="a8c2d-102">Allowing for Identical Duplicate Resources in a Configuration</span></span>

<span data-ttu-id="a8c2d-103">DSC no permite ni administra las definiciones de recursos en conflicto dentro de una configuración.</span><span class="sxs-lookup"><span data-stu-id="a8c2d-103">DSC does not allow or handle conflicting resource definitions within a configuration.</span></span> <span data-ttu-id="a8c2d-104">En lugar de intentar resolver el conflicto, simplemente no funciona.</span><span class="sxs-lookup"><span data-stu-id="a8c2d-104">Instead of trying to resolve the conflict, it simply fails.</span></span> <span data-ttu-id="a8c2d-105">Dado que la reutilización de la configuración se usa más en los recursos compuestos, etc., se producirán conflictos más a menudo.</span><span class="sxs-lookup"><span data-stu-id="a8c2d-105">As configuration reuse becomes more utilized through composite resources, etc. conflicts will occur more often.</span></span> <span data-ttu-id="a8c2d-106">Cuando las definiciones de recursos en conflicto son idénticas, DSC debe ser inteligente y permitirlo.</span><span class="sxs-lookup"><span data-stu-id="a8c2d-106">When conflicting resource definitions are identical, DSC should be smart and allow this.</span></span> <span data-ttu-id="a8c2d-107">En esta versión, se admite tener varias instancias de recursos con definiciones idénticas:</span><span class="sxs-lookup"><span data-stu-id="a8c2d-107">With this release, we support having multiple resource instances that have identical definitions:</span></span>

```powershell
Configuration IIS_FrontEnd
{
    WindowsFeature FE_IIS         #Identical resource
    {
        Ensure = 'Present'
        Name = 'Web-Server'
    }

    WindowsFeature FTP
    {
        Ensure = 'Present'
        Name = 'Web-FTP-Server'
    }
}

Configuration IIS_Worker
{
    WindowsFeature Worker_IIS      #Identical resource
    {
        Ensure = 'Present'
        Name = 'Web-Server'
    }

    WindowsFeature ASP
    {
        Ensure = 'Present'
        Name = 'Web-ASP-Net45'
    }
}

Configuration WebApplication
{
    IIS_Frontend Web {}

    IIS_Worker ASP {}
}
```

<span data-ttu-id="a8c2d-108">En versiones anteriores, el resultado sería un error de compilación debido a un conflicto entre las instancias de WindowsFeature FE_IIS y WindowsFeature Worker_IIS al intentar comprobar la instalación del rol "Servidor web".</span><span class="sxs-lookup"><span data-stu-id="a8c2d-108">In previous releases, the result would be a failed compilation due to a conflict between the WindowsFeature FE_IIS and WindowsFeature Worker_IIS instances trying to ensure the 'Web-Server' role is installed.</span></span> <span data-ttu-id="a8c2d-109">Observe que *todas* las propiedades que se están configurando son idénticas en estas dos configuraciones.</span><span class="sxs-lookup"><span data-stu-id="a8c2d-109">Notice that *all* of the properties that are being configured are identical in these two configurations.</span></span> <span data-ttu-id="a8c2d-110">Puesto que *todas* las propiedades de estos dos recursos son idénticas, el resultado será una compilación correcta.</span><span class="sxs-lookup"><span data-stu-id="a8c2d-110">Since *all* of the properties in these two resources are identical, this will result in a successful compilation now.</span></span> 

<span data-ttu-id="a8c2d-111">Si cualquiera de las propiedades difiere entre los dos recursos, no se considerarán idénticas y se producirá un error de compilación:</span><span class="sxs-lookup"><span data-stu-id="a8c2d-111">If any of the properties are different between the two resources, they will not be considered identical and compilation will fail:</span></span>

```powershell
Configuration IIS_FrontEnd
{
    WindowsFeature FE_IIS
    {
        Ensure = 'Present'     # Ensure is Present here
        Name = 'Web-Server'
    }

    WindowsFeature FTP
    {
        Ensure = 'Present'
        Name = 'Web-FTP-Server'
    }
}

Configuration IIS_Worker
{
    WindowsFeature Worker_IIS
    {
        Ensure = 'Absent'      # Ensure property is Absent instead of Present
        Name = 'Web-Server'
    }

    WindowsFeature ASP
    {
        Ensure = 'Present'
        Name = 'Web-ASP-Net45'
    }
}

Configuration WebApplication
{
    IIS_Frontend Web {}

    IIS_Worker ASP {}
}
```

<span data-ttu-id="a8c2d-112">Esta configuración muy similar se podrá realizarse porque los recursos WindowsFeature FE_IIS y WindowsFeature Worker_IIS ya no son idénticos y, por tanto, están en conflicto.</span><span class="sxs-lookup"><span data-stu-id="a8c2d-112">This very similar configuration will fail because the WindowsFeature FE_IIS and the WindowsFeature Worker_IIS resources are no longer identical and therefore conflict.</span></span>

