---
title: 'Nasıl yapılır: .NET Framework birden çok sürümünde çalışabilecek uygulamaları dağıtmak için ClickOnce kullanma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce applications, multiple .NET Framework versions
- ClickOnce deployment, multiple .NET Framework versions
- deploying applications [ClickOnce], multiple .NET Framework versions
ms.assetid: e0a8c330-21bc-4eb2-b936-fd0f3c3221f1
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 164fe64f360e41c06ef3f7bfd2d8091a6ebefecd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65679942"
---
# <a name="how-to-use-clickonce-to-deploy-applications-that-can-run-on-multiple-versions-of-the-net-framework"></a>Nasıl yapılır: .NET Framework'ün Birden Çok Sürümünde Çalışan Uygulamaları Dağıtmak için ClickOnce'ı Kullanma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

ClickOnce dağıtım teknolojisini kullanarak .NET Framework birden çok sürümünü hedefleyen bir uygulamayı dağıtabilirsiniz. Bunun için uygulama ve dağıtım bildirimlerini oluşturmanız ve güncelleştirmeniz gerekir.  
  
> [!NOTE]
> Uygulamayı .NET Framework birden çok sürümünü hedefleyecek şekilde değiştirmeden önce, uygulamanızın .NET Framework birden çok sürümü ile çalıştığından emin olmanız gerekir. Sürüm ortak dil çalışma zamanı, [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] .NET Framework 2,0, .NET Framework 3,0 ve .NET Framework 3,5 arasında farklıdır.  
  
 Bu işlem aşağıdaki adımları gerektirir:  
  
1. Uygulama ve dağıtım bildirimlerini oluşturun.  
  
2. Dağıtım bildirimini birden çok .NET Framework sürümünü listelemek üzere değiştirin.  
  
3. app.config dosyasını, uyumlu .NET Framework çalışma zamanı sürümlerini listelemek üzere değiştirin.  
  
4. Bağımlı derlemeleri .NET Framework derlemeleri olarak işaretlemek için uygulama bildirimini değiştirin.  
  
5. Uygulama bildirimini imzalayın.  
  
6. Dağıtım bildirimini güncelleştirin ve imzalayın.  
  
### <a name="to-generate-the-application-and-deployment-manifests"></a>Uygulama ve dağıtım bildirimlerini oluşturmak için  
  
- Uygulamayı yayımlamak ve uygulama ve dağıtım bildirim dosyalarını oluşturmak için, proje Tasarımcısı ' nın Yayımla sihirbazını veya Yayımla sayfasını kullanın. Daha fazla bilgi için bkz. [nasıl yapılır: yayımlama sihirbazını veya Yayımla sayfasını kullanarak ClickOnce uygulaması yayımlama](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md) [, proje Tasarımcısı](../ide/reference/publish-page-project-designer.md).  
  
### <a name="to-change-the-deployment-manifest-to-list-the-multiple-net-framework-versions"></a>Dağıtım bildirimini birden çok .NET Framework sürümünü listelemek üzere değiştirmek için  
  
1. Yayımla dizininde, Visual Studio 'da XML düzenleyicisini kullanarak dağıtım bildirimini açın. Dağıtım bildiriminin. Application dosya adı uzantısı vardır.  
  
2. Ve öğeleri arasındaki XML kodunu, `<compatibleFrameworks xmlns="urn:schemas-microsoft-com:clickonce.v2">` `</compatibleFrameworks>` uygulamanız için desteklenen .NET Framework SÜRÜMLERINI listeleyen XML ile değiştirin.  
  
     Aşağıdaki tabloda, kullanılabilir .NET Framework sürümlerinden bazıları ve dağıtım bildirimine ekleyebileceğiniz karşılık gelen XML gösterilmektedir.  
  
    |.NET Framework sürümü|XML|  
    |----------------------------|---------|  
    |4 istemci|\<framework targetVersion="4.0" profile="Client" supportedRuntime="4.0.30319" />|  
    |4 tam|\<framework targetVersion="4.0" profile="Full" supportedRuntime="4.0.30319" />|  
    |3,5 istemcisi|\<framework targetVersion="3.5" profile="Client" supportedRuntime="2.0.50727" />|  
    |3,5 tam|\<framework targetVersion="3.5" profile="Full" supportedRuntime="2.0.50727" />|  
    |3.0|\<framework targetVersion="3.0" supportedRuntime="2.0.50727" />|  
  
### <a name="to-change-the-appconfig-file-to-list-the-compatible-net-framework-runtime-versions"></a>app.config dosyasını, uyumlu .NET Framework çalışma zamanı sürümlerini listelemek üzere değiştirmek için  
  
1. Çözüm Gezgini içinde, Visual Studio 'da XML düzenleyicisini kullanarak App.config dosyasını açın.  
  
2. `<startup>` `</startup>` Uygulamanız için desteklenen .NET Framework çalışma ZAMANLARıNı listeleyen XML ile ve ÖĞELERI arasındaki XML kodunu değiştirin (veya ekleyin).  
  
     Aşağıdaki tabloda, kullanılabilir .NET Framework sürümlerinden bazıları ve dağıtım bildirimine ekleyebileceğiniz karşılık gelen XML gösterilmektedir.  
  
    |.NET Framework çalışma zamanı sürümü|XML|  
    |------------------------------------|---------|  
    |4 istemci|\<supportedRuntime version="v4.0.30319" sku=".NETFramework,Version=v4.0,Profile=Client" />|  
    |4 tam|\<supportedRuntime version="v4.0.30319" sku=".NETFramework,Version=v4.0" />|  
    |3,5 tam|\<supportedRuntime version="v2.0.50727"/>|  
    |3,5 istemcisi|\<supportedRuntime version="v2.0.50727" sku="Client"/>|  
  
### <a name="to-change-the-application-manifest-to-mark-dependent-assemblies-as-net-framework-assemblies"></a>Bağımlı derlemeleri .NET Framework derlemeleri olarak işaretlemek için uygulama bildirimini değiştirme  
  
1. Yayımla dizininde, Visual Studio 'da XML düzenleyicisini kullanarak uygulama bildirimini açın. Dağıtım bildiriminin. manifest dosya adı uzantısı vardır.  
  
2. `group="framework"`Sentinel derlemeler için bağımlılık XML 'e ( `System.Core` ,, `WindowsBase` `Sentinel.v3.5Client` ve) ekleyin `System.Data.Entity` . Örneğin, XML aşağıdaki gibi görünmelidir:  
  
    ```  
    <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" group="framework">  
    ```  
  
3. `<assemblyIdentity>`Microsoft. Windows. CommonLanguageRuntime öğesinin sürüm numarasını en düşük ortak payda olan .NET Framework sürüm numarasına güncelleştirin. Örneğin, uygulama 3,5 .NET Framework hedefliyorsa ve [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] 2.0.50727.0 sürüm numarasını ve XML aşağıdaki gibi görünmelidir:  
  
    ```  
    <dependency>  
      <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true">  
        <assemblyIdentity name="Microsoft.Windows.CommonLanguageRuntime" version="2.0.50727.0" />  
      </dependentAssembly>  
    </dependency>  
    ```  
  
### <a name="to-update-and-re-sign-the-application-and-deployment-manifests"></a>Uygulama ve dağıtım bildirimlerini güncelleştirmek ve yeniden imzalamak için  
  
- Uygulama ve dağıtım bildirimlerini güncelleştirin ve yeniden imzalayın. Daha fazla bilgi için bkz. [nasıl yapılır: uygulama ve dağıtım bildirimlerini yeniden imzalama](../deployment/how-to-re-sign-application-and-deployment-manifests.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ClickOnce uygulamalarını yayımlama](../deployment/publishing-clickonce-applications.md)   
 [\<compatibleFrameworks> Dosyalarında](../deployment/compatibleframeworks-element-clickonce-deployment.md)   
 [\<dependency> Dosyalarında](../deployment/dependency-element-clickonce-application.md)   
 [ClickOnce dağıtım bildirimi](../deployment/clickonce-deployment-manifest.md)   
 [Yapılandırma dosyası şeması](https://msdn.microsoft.com/library/69003d39-dc8a-460c-a6be-e6d93e690b38)
