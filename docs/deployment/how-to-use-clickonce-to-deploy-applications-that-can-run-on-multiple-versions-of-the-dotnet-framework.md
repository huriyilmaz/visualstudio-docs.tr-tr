---
title: Çoklu ClickOnce dağıtmak için ClickOnce'yi kullanma
description: Uygulama dağıtım teknolojisini kullanarak uygulamanın birden çok sürümünü .NET Framework bir uygulamayı ClickOnce öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce applications, multiple .NET Framework versions
- ClickOnce deployment, multiple .NET Framework versions
- deploying applications [ClickOnce], multiple .NET Framework versions
ms.assetid: e0a8c330-21bc-4eb2-b936-fd0f3c3221f1
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- dotnet
ms.openlocfilehash: 0e0e1c010ee1dcf1cc53f37610e518b817a31871
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122096719"
---
# <a name="how-to-use-clickonce-to-deploy-applications-that-can-run-on-multiple-versions-of-the-net-framework"></a>Nasıl kullanılır: .NET framework ClickOnce nin birden çok sürümü üzerinde çalıştırabilirsiniz uygulamaları dağıtmak için ClickOnce'yi kullanma
Dağıtım teknolojisini kullanarak uygulamanın birden çok sürümünü .NET Framework bir ClickOnce dağıtabilirsiniz. Bunun için uygulama ve dağıtım bildirimlerini oluşturmalı ve güncelleştirebilirsiniz.

> [!NOTE]
> Uygulamayı uygulamanın birden çok sürümünü hedef .NET Framework önce, uygulamanın birden çok sürümüyle çalıştırıla olduğundan emin .NET Framework. Ortak dil çalışma zamanı sürümü, .NET Framework 4 ile .NET Framework 2.0, .NET Framework 3.0 ve .NET Framework 3.5 arasında farklıdır.

 Bu işlem için aşağıdaki adımlar gerekir:

1. Uygulama ve dağıtım bildirimlerini oluşturma.

2. Dağıtım bildirimini değiştirarak birden çok .NET Framework listele.

3. Çalışma *app.config* uyumlu çalışma zamanı sürümlerini .NET Framework değiştirme.

4. Bağımlı derlemeleri derlemeler olarak işaretlemek için uygulama bildirimini .NET Framework değiştirme.

5. Uygulama bildirimini imzalar.

6. Dağıtım bildirimini güncelleştirin ve imzalar.

### <a name="to-generate-the-application-and-deployment-manifests"></a>Uygulama ve dağıtım bildirimlerini oluşturmak için

- Uygulamayı yayımlamak ve uygulama ve dağıtım bildirim dosyalarını oluşturmak için Project Tasarımcısı'nın Yayımlama Sihirbazı'nı veya Yayımlama Sayfasını kullanın. Daha fazla bilgi için, [bkz. Nasıl ClickOnce Sihirbazı'nı kullanarak bir ClickOnce](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md) uygulaması yayımlama veya Sayfa [Yayımlama, Project Tasarımcısı.](../ide/reference/publish-page-project-designer.md)

### <a name="to-change-the-deployment-manifest-to-list-the-multiple-net-framework-versions"></a>Dağıtım bildirimini birden çok sürüme göre .NET Framework için

1. Yayımlama dizininde XML Düzenleyicisi'ni kullanarak dağıtım bildirimini Visual Studio. Dağıtım bildiriminin *.application dosya adı* uzantısı vardır.

2. ve öğeleri arasındaki XML `<compatibleFrameworks xmlns="urn:schemas-microsoft-com:clickonce.v2">` `</compatibleFrameworks>` kodunu, uygulamanıza uygun desteklenen .NET Framework XML ile değiştirin.

     Aşağıdaki tabloda, kullanılabilir bazı .NET Framework sürümleri ve dağıtım bildirimine ek oluşturabilecek ilgili XML'i gösterir.

    |.NET Framework sürümü|XML|
    |----------------------------|---------|
    |4 İstemci|\<framework targetVersion="4.0" profile="Client" supportedRuntime="4.0.30319" />|
    |4 Tam|\<framework targetVersion="4.0" profile="Full" supportedRuntime="4.0.30319" />|
    |3.5 İstemci|\<framework targetVersion="3.5" profile="Client" supportedRuntime="2.0.50727" />|
    |3.5 Tam|\<framework targetVersion="3.5" profile="Full" supportedRuntime="2.0.50727" />|
    |3.0|\<framework targetVersion="3.0" supportedRuntime="2.0.50727" />|

### <a name="to-change-the-appconfig-file-to-list-the-compatible-net-framework-runtime-versions"></a>Uyumlu çalışma app.config sürümlerini listelemeyecek şekilde .NET Framework için

1. Bu Çözüm Gezgini xml *düzenleyicisini kullanarakapp.config* dosyasını açın ve Visual Studio.

2. ve öğeleri arasındaki XML kodunu, uygulamanıza yönelik desteklenen çalışma zamanlarını liste .NET Framework `<startup>` `</startup>` XML ile değiştirin (veya ekleyin).

     Aşağıdaki tabloda, kullanılabilir bazı .NET Framework sürümleri ve dağıtım bildirimine ek oluşturabilecek ilgili XML'i gösterir.

    |.NET Framework çalışma zamanı sürümü|XML|
    |------------------------------------|---------|
    |4 İstemci|\<supportedRuntime version="v4.0.30319" sku=".NETFramework,Version=v4.0,Profile=Client" />|
    |4 Tam|\<supportedRuntime version="v4.0.30319" sku=".NETFramework,Version=v4.0" />|
    |3.5 Tam|\<supportedRuntime version="v2.0.50727"/>|
    |3.5 İstemci|\<supportedRuntime version="v2.0.50727" sku="Client"/>|

### <a name="to-change-the-application-manifest-to-mark-dependent-assemblies-as-net-framework-assemblies"></a>Uygulama bildirimini bağımlı derlemeleri bağımsız derlemeler olarak işaret .NET Framework için

1. Yayımlama dizininde XML Düzenleyicisi'ni kullanarak uygulama bildirimini Visual Studio. Dağıtım bildiriminin *.manifest dosya* adı uzantısı vardır.

2. `group="framework"`Sentinel derlemeleri için bağımlılık XML'sini ekleyin ( `System.Core` , , ve `WindowsBase` `Sentinel.v3.5Client` `System.Data.Entity` ). Örneğin, XML aşağıdaki gibi görünüyor:

   ```xml
   <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" group="framework">
   ```

3. `<assemblyIdentity>`Microsoft.Windows için öğesinin sürüm numarasını Windows. CommonLanguageRuntime, en düşük ortak payda olan .NET Framework için sürüm numarasıdır. Örneğin, uygulama .NET Framework 3.5 ve .NET Framework 4'ü hedeflerse, 2.0.50727.0 sürüm numarasını kullanın ve XML aşağıdaki gibi gelsin:

   ```xml
   <dependency>
     <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true">
       <assemblyIdentity name="Microsoft.Windows.CommonLanguageRuntime" version="2.0.50727.0" />
     </dependentAssembly>
   </dependency>
   ```

### <a name="to-update-and-re-sign-the-application-and-deployment-manifests"></a>Uygulama ve dağıtım bildirimlerini güncelleştirmek ve yeniden imzalamak için

- Uygulama ve dağıtım bildirimlerini güncelleştirin ve yeniden imzalar. Daha fazla bilgi için, [bkz. How to: Re-sign application and deployment manifests](../deployment/how-to-re-sign-application-and-deployment-manifests.md).

## <a name="see-also"></a>Ayrıca bkz.
- [ClickOnce uygulamalarını yayımlama](../deployment/publishing-clickonce-applications.md)
- [\<compatibleFrameworks> Öğe](../deployment/compatibleframeworks-element-clickonce-deployment.md)
- [\<dependency> Öğe](../deployment/dependency-element-clickonce-application.md)
- [ClickOnce dağıtım bildirimi](../deployment/clickonce-deployment-manifest.md)
- [Yapılandırma dosyası şeması](/dotnet/framework/configure-apps/file-schema/index)
