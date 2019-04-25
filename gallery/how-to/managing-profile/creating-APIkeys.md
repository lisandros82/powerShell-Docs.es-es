---
ms.date: 09/10/2018
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: Administración de claves de API
ms.openlocfilehash: 954eb27c25babdb8efe50c13caf5f2d287c6b3e3
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084365"
---
# <a name="managing-api-keys"></a><span data-ttu-id="44d72-103">Administración de claves de API</span><span class="sxs-lookup"><span data-stu-id="44d72-103">Managing API keys</span></span>

<span data-ttu-id="44d72-104">La Galería de PowerShell admite la creación de varias claves de API para admitir toda una variedad de requisitos de publicación.</span><span class="sxs-lookup"><span data-stu-id="44d72-104">The PowerShell Gallery supports creating multiple API keys to support a range of publishing requirements.</span></span> <span data-ttu-id="44d72-105">Una clave de API puede aplicar a uno o varios paquetes, concede privilegios específicos y tiene una fecha de expiración.</span><span class="sxs-lookup"><span data-stu-id="44d72-105">An API key can apply to one or more packages, grants specific privileges, and has an expiration date.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="44d72-106">Los usuarios que publicaron en la Galería de PowerShell antes de la introducción de claves de API con ámbito tendrán una "clave de API de acceso completo".</span><span class="sxs-lookup"><span data-stu-id="44d72-106">Users who published to the PowerShell Gallery prior to the introduction of scoped API keys will have a "Full access API key".</span></span> <span data-ttu-id="44d72-107">Las claves de acceso completo no tienen las mejoras de seguridad que están integradas en las claves de API con ámbito.</span><span class="sxs-lookup"><span data-stu-id="44d72-107">The full access keys do not have the security improvements built into scoped API keys.</span></span> <span data-ttu-id="44d72-108">Las claves de acceso completo nunca expiran y se aplican a todos lo que pertenece al usuario.</span><span class="sxs-lookup"><span data-stu-id="44d72-108">The full access keys never expires and apply to everything owned by the user.</span></span> <span data-ttu-id="44d72-109">Si se elimina esta clave, no se puede volver a crear.</span><span class="sxs-lookup"><span data-stu-id="44d72-109">If you delete this key, it cannot be recreated.</span></span>

<span data-ttu-id="44d72-110">En esta imagen se muestran las opciones disponibles al crear una clave de API con ámbito.</span><span class="sxs-lookup"><span data-stu-id="44d72-110">The following image shows the options available when creating a scoped API key.</span></span>

![Crear claves de API](../../Images/PSGallery_KeyScoped.png)

<span data-ttu-id="44d72-112">En este ejemplo, hemos creado una clave de API denominada **AzureRMDataFactory**.</span><span class="sxs-lookup"><span data-stu-id="44d72-112">In this example, we created an API key named **AzureRMDataFactory**.</span></span> <span data-ttu-id="44d72-113">Este valor de clave puede usarse para insertar paquetes con nombres que empiecen por 'AzureRM.DataFactory' y es válido durante 365 días.</span><span class="sxs-lookup"><span data-stu-id="44d72-113">This key value can be used to push packages with names that begin with 'AzureRM.DataFactory' and is valid for 365 days.</span></span> <span data-ttu-id="44d72-114">Este es un escenario típico en el que los distintos equipos de la misma organización trabajan en paquetes diferentes.</span><span class="sxs-lookup"><span data-stu-id="44d72-114">This is a typical scenario when different teams within the same organization work on different packages.</span></span> <span data-ttu-id="44d72-115">Los miembros del equipo tienen una clave que les concede privilegios para el paquete específico en el que trabajan.</span><span class="sxs-lookup"><span data-stu-id="44d72-115">The members of the team have a key that grants them privileges for the specific package they work on.</span></span>
<span data-ttu-id="44d72-116">El valor de expiración impide el uso de claves obsoletas u olvidadas.</span><span class="sxs-lookup"><span data-stu-id="44d72-116">The expiration value prevents the use of stale or forgotten keys.</span></span>

## <a name="using-glob-patterns"></a><span data-ttu-id="44d72-117">Uso de patrones globales</span><span class="sxs-lookup"><span data-stu-id="44d72-117">Using glob patterns</span></span>

<span data-ttu-id="44d72-118">Si trabaja en varios paquetes, puede usar patrones globales para hacer coincidir varios paquetes como un grupo.</span><span class="sxs-lookup"><span data-stu-id="44d72-118">If you work on multiple packages, you can use globbing patterns to match multiple packages as a group.</span></span> <span data-ttu-id="44d72-119">Los permisos de clave de API se aplican a todos los nuevos paquetes que coincidan con el patrón global.</span><span class="sxs-lookup"><span data-stu-id="44d72-119">API key permissions apply to all new packages matching the glob pattern.</span></span> <span data-ttu-id="44d72-120">Por ejemplo, en el ejemplo anterior se usa el valor 'AzureRM.DataFactory\*' para **Patrón global**.</span><span class="sxs-lookup"><span data-stu-id="44d72-120">For example, the previous example uses a **Glob Pattern** value of 'AzureRM.DataFactory\*'.</span></span> <span data-ttu-id="44d72-121">Puede insertar un paquete denominado 'AzureRm.DataFactoryV2.Netcore' con esta clave, puesto que el paquete coincide con el patrón global.</span><span class="sxs-lookup"><span data-stu-id="44d72-121">You can push a package named 'AzureRm.DataFactoryV2.Netcore' using this key since the package matches the glob pattern.</span></span>

## <a name="create-api-keys-securely"></a><span data-ttu-id="44d72-122">Crear claves de API de forma segura</span><span class="sxs-lookup"><span data-stu-id="44d72-122">Create API keys securely</span></span>

<span data-ttu-id="44d72-123">Por motivos de seguridad, un valor de clave recién creado nunca se muestra en la pantalla y solo está disponible con el botón Copiar, como se muestra aquí.</span><span class="sxs-lookup"><span data-stu-id="44d72-123">For security, a newly created key value is never shown on the screen and is only available with the Copy button, as shown below.</span></span>

![Obtener el nuevo valor de clave de API](../../Images/PSGallery_CopyCreatedKey.png)

> [!IMPORTANT]
> <span data-ttu-id="44d72-125">Solo se puede copiar el valor de clave de API inmediatamente después de crearlo o actualizarlo.</span><span class="sxs-lookup"><span data-stu-id="44d72-125">You can only copy the API key value immediately after creating or refreshing it.</span></span> <span data-ttu-id="44d72-126">No se mostrará y no se podrá acceder a él de nuevo después de actualizar la página.</span><span class="sxs-lookup"><span data-stu-id="44d72-126">It will not be displayed, and will not be accessible again after the page is refreshed.</span></span> <span data-ttu-id="44d72-127">Si pierde el valor de clave, debe usar la función Regenerar y copiar la clave después de regenerarla de nuevo.</span><span class="sxs-lookup"><span data-stu-id="44d72-127">If you lose the key value, you must use Regenerate, and copy the key after it is regenerated.</span></span>

## <a name="key-permissions-and-expiration"></a><span data-ttu-id="44d72-128">Expiración y permisos de clave</span><span class="sxs-lookup"><span data-stu-id="44d72-128">Key permissions and expiration</span></span>

<span data-ttu-id="44d72-129">Las claves de API con ámbito pueden asignar cualquiera de los siguientes permisos:</span><span class="sxs-lookup"><span data-stu-id="44d72-129">Scoped API keys can assign any of the following permissions:</span></span>

- <span data-ttu-id="44d72-130">Insertar nuevos paquetes</span><span class="sxs-lookup"><span data-stu-id="44d72-130">Push new packages</span></span>
- <span data-ttu-id="44d72-131">Insertar paquetes nuevos o actualizados</span><span class="sxs-lookup"><span data-stu-id="44d72-131">Push new or update packages</span></span>
- <span data-ttu-id="44d72-132">Quitar paquetes de la lista</span><span class="sxs-lookup"><span data-stu-id="44d72-132">Unlist packages</span></span>

<span data-ttu-id="44d72-133">Cada clave nueva tiene una fecha de expiración.</span><span class="sxs-lookup"><span data-stu-id="44d72-133">Every new key has an expiration.</span></span> <span data-ttu-id="44d72-134">El valor de expiración se mide en días.</span><span class="sxs-lookup"><span data-stu-id="44d72-134">The expiration value is measured in days.</span></span> <span data-ttu-id="44d72-135">Los valores posibles para la expiración son:</span><span class="sxs-lookup"><span data-stu-id="44d72-135">The possible values for expiration are:</span></span>

- <span data-ttu-id="44d72-136">1 día</span><span class="sxs-lookup"><span data-stu-id="44d72-136">1 day</span></span>
- <span data-ttu-id="44d72-137">90 días</span><span class="sxs-lookup"><span data-stu-id="44d72-137">90 days</span></span>
- <span data-ttu-id="44d72-138">180 días</span><span class="sxs-lookup"><span data-stu-id="44d72-138">180 days</span></span>
- <span data-ttu-id="44d72-139">270 días</span><span class="sxs-lookup"><span data-stu-id="44d72-139">270 days</span></span>
- <span data-ttu-id="44d72-140">365 días (valor predeterminado)</span><span class="sxs-lookup"><span data-stu-id="44d72-140">365 days (default)</span></span>

<span data-ttu-id="44d72-141">Esta configuración no puede cambiarse una vez creada la clave.</span><span class="sxs-lookup"><span data-stu-id="44d72-141">These settings cannot be changed once the key is created.</span></span> <span data-ttu-id="44d72-142">No se puede crear una nueva clave que no expira nunca.</span><span class="sxs-lookup"><span data-stu-id="44d72-142">You cannot create a new key that never expires.</span></span>

## <a name="editing-and-deleting-existing-api-keys"></a><span data-ttu-id="44d72-143">Editar y eliminar claves de API existentes</span><span class="sxs-lookup"><span data-stu-id="44d72-143">Editing and deleting existing API keys</span></span>

<span data-ttu-id="44d72-144">Puede cambiar algunos valores de una clave existente.</span><span class="sxs-lookup"><span data-stu-id="44d72-144">You can change some settings of an existing key.</span></span> <span data-ttu-id="44d72-145">Como se indicó anteriormente, no se puede modificar el ámbito de seguridad para una clave de API existente o cambiar la expiración.</span><span class="sxs-lookup"><span data-stu-id="44d72-145">As previously noted, you cannot modify the security scope for an existing API key or change the expiration.</span></span> <span data-ttu-id="44d72-146">En la captura de pantalla siguiente se muestran las opciones que pueden cambiarse:</span><span class="sxs-lookup"><span data-stu-id="44d72-146">The changeable options are shown in the following screenshot:</span></span>

![Obtener el nuevo valor de clave de API](../../Images/PSGallery_EditAPIKey.png)

<span data-ttu-id="44d72-148">Para cambiar los paquetes controlados por una clave, puede elegir paquetes individuales de la lista o cambiar el patrón global.</span><span class="sxs-lookup"><span data-stu-id="44d72-148">To change the packages controlled by a key, you can choose individual packages from the list or change the glob pattern.</span></span>

<span data-ttu-id="44d72-149">Al hacer clic en **Regenerar** se crea un nuevo valor de clave.</span><span class="sxs-lookup"><span data-stu-id="44d72-149">Clicking **Regenerate** creates a new key value.</span></span> <span data-ttu-id="44d72-150">Al igual que cuando creó inicialmente la clave, también deberá **Copiar** el valor de clave inmediatamente después de actualizarlo.</span><span class="sxs-lookup"><span data-stu-id="44d72-150">Just like when you initially created the key, you must **Copy** the key value immediately after updating it.</span></span> <span data-ttu-id="44d72-151">La opción **Copiar** no está disponible una vez que se sale de esta página.</span><span class="sxs-lookup"><span data-stu-id="44d72-151">The **Copy** option is not available once you leave this page.</span></span>

<span data-ttu-id="44d72-152">Al hacer clic en **Eliminar** se muestra un mensaje de confirmación.</span><span class="sxs-lookup"><span data-stu-id="44d72-152">Clicking **Delete** displays a confirmation message.</span></span> <span data-ttu-id="44d72-153">Una vez que se elimina una clave, no se puede usar.</span><span class="sxs-lookup"><span data-stu-id="44d72-153">Once a key is deleted, it will be unusable.</span></span>

## <a name="key-expiration"></a><span data-ttu-id="44d72-154">Expiración de claves</span><span class="sxs-lookup"><span data-stu-id="44d72-154">Key expiration</span></span>

<span data-ttu-id="44d72-155">Diez días antes de la expiración, la Galería de PowerShell envía un mensaje de advertencia al titular de la cuenta de la clave de API.</span><span class="sxs-lookup"><span data-stu-id="44d72-155">Ten days before the expiration, the PowerShell Gallery sends a warning email the account holder of the API key.</span></span> <span data-ttu-id="44d72-156">Tras la expiración, la clave queda inutilizable.</span><span class="sxs-lookup"><span data-stu-id="44d72-156">After expiration, the key is unusable.</span></span> <span data-ttu-id="44d72-157">Se muestra un mensaje de advertencia en la parte superior de la página de administración de claves de API que muestra qué claves ya no son válidas.</span><span class="sxs-lookup"><span data-stu-id="44d72-157">A warning message is displayed at the top of the API key management page showing which keys are no longer valid.</span></span> <span data-ttu-id="44d72-158">Puede generar un nuevo valor de clave.</span><span class="sxs-lookup"><span data-stu-id="44d72-158">You can generate a new key value.</span></span>
