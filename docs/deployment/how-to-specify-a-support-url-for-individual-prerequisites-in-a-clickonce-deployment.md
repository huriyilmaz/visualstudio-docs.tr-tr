---
title: ClickOnce dağıtımında Önkoşullar için destek URL 'SI
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, prerequisites
- ClickOnce deployment, URLs
ms.assetid: 590742c3-a286-4160-aa75-7a441bb2207b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bf474e4926403a9475860bfdc620ee4a6860f8aa
ms.sourcegitcommit: 3f491903e0c10db9a3f3fc0940f7b587fcbf9530
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85381736"
---
# <a name="how-to-specify-a-support-url-for-individual-prerequisites-in-a-clickonce-deployment"></a>Nasıl yapılır: bir ClickOnce dağıtımında tek Önkoşullar için destek URL 'SI belirtme
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]Dağıtım, uygulamanın çalışması için istemci bilgisayarda kullanılabilir olması gereken bazı önkoşulları test edebilir [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] . Bu bağımlılıklar, .NET Framework gereken en düşük sürümü, işletim sisteminin sürümünü ve genel derleme önbelleğinde (GAC) önceden yüklenmiş olması gereken tüm derlemeleri içerir. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]Ancak, bu önkoşullardan herhangi biri yüklenemez; bir önkoşul bulunamazsa, yüklemeyi durdurur ve yüklemenin neden başarısız olduğunu açıklayan bir iletişim kutusu görüntüler.

 Önkoşulları yüklemek için iki yöntem vardır. Bunları bir önyükleyici uygulaması kullanarak yükleyebilirsiniz. Alternatif olarak, önkoşul bulunamazsa, iletişim kutusunda kullanıcılara görüntülenecek olan ayrı Önkoşullar için bir destek URL 'SI belirtebilirsiniz. Bu URL tarafından başvurulan sayfa, gerekli önkoşulu yüklemek için yönergelerin bağlantılarını içerebilir. Bir uygulama tek bir önkoşul için destek URL 'SI belirtmezse, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] tanımlanmazsa uygulamanın dağıtım bildiriminde belirtilen destek URL 'sini bir bütün olarak görüntüler.

 Ancak [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , *Mage.exe*ve *MageUI.exe* her türlü dağıtım oluşturmak için kullanılabilir [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] , bu araçların hiçbiri ayrı Önkoşullar için bir destek URL 'si belirtmeyi doğrudan desteklemez. Bu belgede, bu destek URL 'Lerini dahil etmek için dağıtımınızın uygulama bildirimi ve dağıtım bildiriminin nasıl değiştirileceği açıklanmaktadır.

### <a name="specify-a-support-url-for-an-individual-prerequisite"></a>Tek bir önkoşul için destek URL 'SI belirtin

1. Uygulamanın uygulama bildirimini ( *. manifest* dosyası) [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] bir metin düzenleyicisinde açın.

2. Bir işletim sistemi önkoşulu için, `supportUrl` özniteliğini `dependentOS` öğesine ekleyin:

   ```xml
    <dependency>
       <dependentOS supportUrl="http://www.adatum.com/MyApplication/wrongOSFound.htm">
         <osVersionInfo>
           <os majorVersion="5" minorVersion="1" buildNumber="2600" servicePackMajor="0" servicePackMinor="0" />
         </osVersionInfo>
       </dependentOS>
     </dependency>
   ```

3. Ortak dil çalışma zamanının belirli bir sürümüne yönelik bir önkoşul için, `supportUrl` özniteliğini `dependentAssembly` ortak dil çalışma zamanı bağımlılığını belirten girdiye ekleyin:

   ```xml
     <dependency>
       <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" supportUrl=" http://www.adatum.com/MyApplication/wrongClrVersionFound.htm">
         <assemblyIdentity name="Microsoft.Windows.CommonLanguageRuntime" version="4.0.30319.0" />
       </dependentAssembly>
     </dependency>
   ```

4. Genel derleme önbelleğinde önceden yüklenmiş olması gereken bir derlemeye yönelik önkoşul için, `supportUrl` `dependentAssembly` gerekli derlemeyi belirten öğesi için öğesini ayarlayın:

   ```xml
     <dependency>
       <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" supportUrl=" http://www.adatum.com/MyApplication/missingSampleGACAssembly.htm">
         <assemblyIdentity name="SampleGACAssembly" version="5.0.0.0" publicKeyToken="04529dfb5da245c5" processorArchitecture="msil" language="neutral" />
       </dependentAssembly>
     </dependency>
   ```

5. İsteğe bağlı. .NET Framework 4 ' ü hedefleyen uygulamalar için, bir metin düzenleyicisinde uygulamanın dağıtım bildirimini ( *. Application* dosyası) açın [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] .

6. .NET Framework 4 önkoşulu için, `supportUrl` özniteliğini `compatibleFrameworks` öğesine ekleyin:

   ```xml
   <compatibleFrameworks  xmlns="urn:schemas-microsoft-com:clickonce.v2" supportUrl="http://adatum.com/MyApplication/CompatibleFrameworks.htm">
     <framework targetVersion="4.0" profile="Client" supportedRuntime="4.0.30319" />
     <framework targetVersion="4.0" profile="Full" supportedRuntime="4.0.30319" />
   </compatibleFrameworks>
   ```

7. Uygulama bildirimini el ile değiştirdiyseniz, dijital sertifikanızı kullanarak uygulama bildirimini yeniden imzalamanız, sonra da dağıtım bildirimini güncelleştirip yeniden imzalamanız gerekir. Bu görevleri gerçekleştirmek için *Mage.exe* veya *MageUI.exe* SDK araçlarını kullanın, bu dosyaların yeniden oluşturulması [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] el ile yaptığınız değişiklikleri siler. Bildirimleri yeniden imzalamak için Mage.exe kullanma hakkında daha fazla bilgi için bkz. [nasıl yapılır: uygulama ve dağıtım bildirimlerini yeniden imzalama](../deployment/how-to-re-sign-application-and-deployment-manifests.md).

## <a name="net-framework-security"></a>.NET Framework güvenliği
 Uygulama kısmi güvende çalışmak üzere işaretlenmişse, iletişim kutusunda Destek URL 'SI görüntülenmez.

## <a name="see-also"></a>Ayrıca bkz.
- [Mage.exe (Bildirim Oluşturma ve Düzenleme Aracı)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)
- [İzlenecek yol: ClickOnce uygulamasını el ile dağıtma](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)
- [\<compatibleFrameworks>dosyalarında](../deployment/compatibleframeworks-element-clickonce-deployment.md)
- [ClickOnce ve Authenticode](../deployment/clickonce-and-authenticode.md)
- [Uygulama dağıtımının önkoşulları](../deployment/application-deployment-prerequisites.md)