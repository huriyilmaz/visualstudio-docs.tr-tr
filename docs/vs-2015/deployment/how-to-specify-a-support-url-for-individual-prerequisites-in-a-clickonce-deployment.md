---
title: "Nasıl yapılır: bir ClickOnce dağıtımında tek Önkoşullar için destek URL 'SI belirtme | Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, prerequisites
- ClickOnce deployment, URLs
ms.assetid: 590742c3-a286-4160-aa75-7a441bb2207b
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1907b619bcc616c73d9b9e37af30722c02bf100e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65679967"
---
# <a name="how-to-specify-a-support-url-for-individual-prerequisites-in-a-clickonce-deployment"></a>Nasıl yapılır: Bir ClickOnce Dağıtımı'nda Bağımsız Önkoşullar için Destek URL'sini Belirtme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]Dağıtım, uygulamanın çalışması için istemci bilgisayarda kullanılabilir olması gereken bazı önkoşulları test edebilir [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] . Bunlar, öğesinin gerekli en düşük sürümünü [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] , işletim sisteminin sürümünü ve genel derleme önbelleğinde (GAC) önceden yüklenmiş olması gereken tüm derlemeleri içerir. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]Ancak, bu önkoşullardan herhangi biri yüklenemez; bir önkoşul bulunamazsa, yüklemeyi durdurur ve yüklemenin neden başarısız olduğunu açıklayan bir iletişim kutusu görüntüler.  
  
 Önkoşulları yüklemek için iki yöntem vardır. Bunları bir önyükleyici uygulaması kullanarak yükleyebilirsiniz. Alternatif olarak, önkoşul bulunamazsa, iletişim kutusunda kullanıcılara görüntülenecek olan ayrı Önkoşullar için bir destek URL 'SI belirtebilirsiniz. Bu URL tarafından başvurulan sayfa, gerekli önkoşulu yüklemek için yönergelerin bağlantılarını içerebilir. Bir uygulama tek bir önkoşul için destek URL 'SI belirtmezse, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] tanımlanmazsa uygulamanın dağıtım bildiriminde belirtilen destek URL 'sini bir bütün olarak görüntüler.  
  
 Ancak [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , Mage.exe ve MageUI.exe her türlü dağıtım oluşturmak için kullanılabilir [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] , bu araçların hiçbiri ayrı Önkoşullar için bir destek URL 'si belirtmeyi doğrudan desteklemez. Bu belgede, bu destek URL 'Lerini dahil etmek için dağıtımınızın uygulama bildirimi ve dağıtım bildiriminin nasıl değiştirileceği açıklanmaktadır.  
  
### <a name="specifying-a-support-url-for-an-individual-prerequisite"></a>Tek bir önkoşul için destek URL 'SI belirtme  
  
1. Uygulamanızın uygulama bildirimini (. manifest dosyası) [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] bir metin düzenleyicisinde açın.  
  
2. Bir işletim sistemi önkoşulu için, `supportUrl` özniteliğini `dependentOS` öğesine ekleyin:  
  
    ```  
     <dependency>  
        <dependentOS supportUrl="http://www.adatum.com/MyApplication/wrongOSFound.htm">  
          <osVersionInfo>  
            <os majorVersion="5" minorVersion="1" buildNumber="2600" servicePackMajor="0" servicePackMinor="0" />  
          </osVersionInfo>  
        </dependentOS>  
      </dependency>  
    ```  
  
3. Ortak dil çalışma zamanının belirli bir sürümüne yönelik bir önkoşul için, `supportUrl` özniteliğini `dependentAssembly` ortak dil çalışma zamanı bağımlılığını belirten girdiye ekleyin:  
  
    ```  
      <dependency>  
        <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" supportUrl=" http://www.adatum.com/MyApplication/wrongClrVersionFound.htm">  
          <assemblyIdentity name="Microsoft.Windows.CommonLanguageRuntime" version="4.0.30319.0" />  
        </dependentAssembly>  
      </dependency>  
    ```  
  
4. Genel derleme önbelleğinde önceden yüklenmiş olması gereken bir derlemeye yönelik önkoşul için, `supportUrl` `dependentAssembly` gerekli derlemeyi belirten öğesi için öğesini ayarlayın:  
  
    ```  
      <dependency>  
        <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" supportUrl=" http://www.adatum.com/MyApplication/missingSampleGACAssembly.htm">  
          <assemblyIdentity name="SampleGACAssembly" version="5.0.0.0" publicKeyToken="04529dfb5da245c5" processorArchitecture="msil" language="neutral" />  
        </dependentAssembly>  
      </dependency>  
    ```  
  
5. İsteğe bağlı. .NET Framework 4 ' ü hedefleyen uygulamalar için, uygulamanızın dağıtım bildirimini (. Application dosyası) [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] bir metin düzenleyicisinde açın.  
  
6. .NET Framework 4 önkoşulu için, `supportUrl` özniteliğini `compatibleFrameworks` öğesine ekleyin:  
  
    ```  
    <compatibleFrameworks  xmlns="urn:schemas-microsoft-com:clickonce.v2" supportUrl="http://adatum.com/MyApplication/CompatibleFrameworks.htm">  
      <framework targetVersion="4.0" profile="Client" supportedRuntime="4.0.30319" />  
      <framework targetVersion="4.0" profile="Full" supportedRuntime="4.0.30319" />  
    </compatibleFrameworks>  
    ```  
  
7. Uygulama bildirimini el ile değiştirdiyseniz, dijital sertifikanızı kullanarak uygulama bildirimini yeniden imzalamanız, sonra da dağıtım bildirimini güncelleştirip yeniden imzalamanız gerekir. Bu görevi gerçekleştirmek için Mage.exe veya MageUI.exe SDK araçlarını kullanmanız gerekir, bu dosyaların yeniden oluşturulması [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] el ile yaptığınız değişiklikleri siler. Bildirimleri yeniden imzalamak için Mage.exe kullanma hakkında daha fazla bilgi için bkz. [nasıl yapılır: uygulama ve dağıtım bildirimlerini yeniden imzalama](../deployment/how-to-re-sign-application-and-deployment-manifests.md).  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Uygulama kısmi güvende çalışmak üzere işaretlenmişse, iletişim kutusunda Destek URL 'SI görüntülenmez.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Mage.exe (Bildirim Oluşturma ve Düzenleme Aracı)](https://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1)   
 [İzlenecek yol: ClickOnce uygulamasını El Ile dağıtma](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)   
 [\<compatibleFrameworks> Dosyalarında](../deployment/compatibleframeworks-element-clickonce-deployment.md)   
 [ClickOnce ve Authenticode](../deployment/clickonce-and-authenticode.md)   
 [Uygulama dağıtımı önkoşulları](../deployment/application-deployment-prerequisites.md)
