---
title: Güvenlik/sürüm oluşturma/bildirim sorunları (ClickOnce)
description: ClickOnce dağıtımının başarısız olmasına neden olabilecek ClickOnce güvenliği, uygulama sürümü oluşturma ve bildirim sözdizimi ve semantiğinin sorunları hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- versioning, ClickOnce applications
- ClickOnce applications, Windows Vista User Account Control
- ClickOnce applications, versioning issues
- security, ClickOnce applications
- Windows 7, ClickOnce deployments
- ClickOnce applications, manifest issues
- User Account Control, ClickOnce applications
- Windows Vista, ClickOnce deployments
- manifests [ClickOnce]
- ClickOnce applications, security issues
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 55758f67c845cbf753d51ebfb94b87af6cf55cde
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99877635"
---
# <a name="security-versioning-and-manifest-issues-in-clickonce-deployments"></a>ClickOnce dağıtımlarında güvenlik, sürüm ve bildirim sorunları

[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]Güvenlik, uygulama sürümü oluşturma ve bildirim söz dizimi ve semantiğinin, dağıtımın başarılı olmasına neden olabilecek çeşitli sorunlar vardır [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] .

## <a name="clickonce-and-windows-vista-user-account-control"></a>ClickOnce ve Windows Vista Kullanıcı hesabı denetimi

' De [!INCLUDE[windowsver](../deployment/includes/windowsver_md.md)] , geçerli kullanıcı yönetici izinlerine sahip bir hesapla oturum açmış olsa bile, varsayılan olarak uygulamalar standart Kullanıcı olarak çalışır. Bir uygulama yönetici izinleri gerektiren bir eylem gerçekleştirmelidir, bu, işletim sistemine bildirir ve ardından kullanıcıdan yönetici kimlik bilgilerini girmesini ister. Kullanıcı hesabı denetimi (UAC) olarak adlandırılan bu özellik, uygulamaların, kullanıcının açık onayı olmadan tüm işletim sistemini etkileyebilecek değişiklikler yapmasını engeller. Windows uygulamaları, `requestedExecutionLevel` uygulama bildirimlerinin bölümünde özniteliğini belirterek bu izin yükseltmesini gerektirdiğini bildirir `trustInfo` .

Uygulamaları güvenlik yükseltmesi saldırılarına sunma riski nedeniyle, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] istemci IÇIN UAC etkinleştirildiyse, uygulamalar izin yükseltmesi isteyememelidir. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]Özniteliğini olarak ayarlamayı deneyen herhangi bir uygulama `requestedExecutionLevel` `requireAdministrator` `highestAvailable` , veya yüklemez [!INCLUDE[windowsver](../deployment/includes/windowsver_md.md)] .

Bazı durumlarda [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulamanız, üzerinde yükleyici algılama mantığı nedeniyle yönetici izinleriyle çalışmayı deneyebilir [!INCLUDE[windowsver](../deployment/includes/windowsver_md.md)] . Bu durumda, `requestedExecutionLevel` uygulama bildiriminde özniteliğini olarak ayarlayabilirsiniz `asInvoker` . Bu, uygulamanın kendisinin yükseltme olmadan çalışmasına neden olur. [!INCLUDE[vs_orcas_long](../debugger/includes/vs_orcas_long_md.md)] Bu özniteliği tüm uygulama bildirimlerine otomatik olarak ekler.

Uygulamanın tüm kullanım ömrü boyunca yönetici izinleri gerektiren bir uygulama geliştiriyorsanız, bunun yerine Windows Installer (MSI) teknolojisini kullanarak uygulamayı dağıtmanız gerekir. Daha fazla bilgi için bkz. [Windows Installer temel kavramları](../extensibility/internals/windows-installer-basics.md).

## <a name="online-application-quotas-and-partial-trust-applications"></a>Çevrimiçi uygulama kotaları ve kısmi güven uygulamaları

[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]Uygulamanız bir yükleme yerine çevrimiçi çalışırsa, çevrimiçi uygulamalar için ayrılan kota kümesine sığmalıdır. Ayrıca, kısıtlı güvenlik izinleri kümesi gibi kısmi güvende çalışan bir ağ uygulaması, kota boyutunun yarısından daha büyük olamaz.

Daha fazla bilgi ve çevrimiçi uygulama kotasının nasıl değiştirileceği hakkında yönergeler için bkz. [ClickOnce önbelleğine genel bakış](../deployment/clickonce-cache-overview.md).

## <a name="versioning-issues"></a>Sürüm oluşturma sorunları

Derlemenize tanımlayıcı adlar atarsanız ve derleme sürüm numarasını bir uygulama güncelleştirmesini yansıtacak şekilde arttırırsanız sorunlarla karşılaşabilirsiniz. Tanımlayıcı adlı bir derlemeye başvuru ile derlenen herhangi bir derlemenin kendisi yeniden derlenmesi gerekir veya derleme eski sürüme başvurmayı dener. Derleme, bağlama isteğinde eski sürüm değerini kullandığından, bu işlemi deneyecek.

Örneğin, 1.0.0.0 sürümü olan kendi projesinde tanımlayıcı adlı bir derlemeniz olduğunu varsayalım. Derlemeyi derledikten sonra, ana uygulamanızı içeren projeye bir başvuru olarak eklersiniz. Derlemeyi güncelleştirir, sürümü 1.0.0.1 olarak artırın ve uygulamayı yeniden derlemeden dağıtmayı denerseniz, uygulama derlemeyi çalışma zamanında yükleyemez.

Bu hata yalnızca [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] bildirimlerinizi el ile düzenlediğinizde oluşabilir; Visual Studio kullanarak dağıtımınızı oluşturursanız bu hatayla karşılaşmamalıdır.

## <a name="specify-individual-net-framework-assemblies-in-the-manifest"></a>Bildirimde bireysel .NET Framework derlemeleri belirtin

Dağıtımı, bir [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] .NET Framework derlemesinin daha eski bir sürümüne başvuracak şekilde el ile düzenlediyseniz, uygulamanız yükleme başarısız olur. Örneğin, bildirimde belirtilen sürümden önceki bir .NET Framework sürümü için System.Net derlemesine bir başvuru eklediyseniz bir hata oluşur. Genel olarak, uygulamanızın çalıştırıldığı .NET Framework sürümü uygulama bildiriminde bir bağımlılık olarak belirtildiğinde, her bir .NET Framework derlemesine yönelik başvuruları belirtmeye çalışmamalısınız.

## <a name="manifest-parsing-issues"></a>Bildirim ayrıştırma sorunları

Tarafından kullanılan bildirim dosyaları [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] XML dosyalarıdır ve her ikisi de iyi biçimlendirilmiş ve geçerli olmalıdır: XML sözdizimi kurallarına uymaları ve yalnızca ılgılı XML şemasında tanımlanmış öğeleri ve öznitelikleri kullanması gerekir.

Bir bildirim dosyasında sorun oluşmasına neden olabilecek bir şey, uygulamanız için tek veya çift tırnak işareti gibi özel bir karakter içeren bir ad seçmektir. Uygulamanın adı, kimliğinin bir parçasıdır [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] . [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Şu anda özel karakterler içeren kimlikleri ayrıştırmıyor. Uygulamanız etkinleştirilemezse, ad için yalnızca alfabetik ve sayısal karakterler kullandığınızdan emin olun ve yeniden dağıtmayı deneyin.

Dağıtımınızı veya uygulama bildirimlerinizi el ile düzenlediyseniz, istemeden onları bozmuş olabilirsiniz. Bozuk bildirim, doğru bir [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] yüklemeyi engelleyecek. **ClickOnce hatası** Iletişim kutusunda **Ayrıntılar** ' a tıklayarak ve günlükteki hata iletisini okuyarak, çalışma zamanında bu tür hatalara hata ayıklayabilirsiniz. Günlükte aşağıdaki iletilerden biri listelenir:

- Söz dizimi hatasının açıklaması ve hatanın gerçekleştiği satır numarası ve karakter konumu.

- Bildirimin şemasını ihlal etmek için kullanılan bir öğenin veya özniteliğin adı. Bildirimlerinizde el ile XML eklediyseniz, eklemelerinizi bildirim şemalarıyla karşılaştırmanız gerekir. Daha fazla bilgi için bkz. [ClickOnce dağıtım bildirimi](../deployment/clickonce-deployment-manifest.md) ve [ClickOnce uygulama bildirimi](../deployment/clickonce-application-manifest.md).

- KIMLIK çakışması. Dağıtım ve uygulama bildirimlerinde bağımlılık başvuruları, hem hem de özniteliklerinin benzersiz olması `name` gerekir `publicKeyToken` . Her iki öznitelik de bir bildirimde bulunan iki öğe arasında eşleşiyorsa, bildirim ayrıştırma başarısız olur.

## <a name="precautions-when-manually-changing-manifests-or-applications"></a>Bildirimleri veya uygulamaları el ile değiştirme önlemleri

Bir uygulama bildirimini güncelleştirdiğinizde, hem uygulama bildirimini hem de dağıtım bildirimini yeniden imzalamanız gerekir. Dağıtım bildirimi, bu dosyanın karmasını ve onun dijital imzasını içeren uygulama bildirimine bir başvuru içerir.

### <a name="precautions-with-deployment-provider-usage"></a>Dağıtım sağlayıcısı kullanımıyla ilgili önlemler

[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]Dağıtım bildiriminin, `deploymentProvider` uygulamanın yüklenmesi ve hizmet verilmesi gereken konumun tam yolunu işaret eden bir özelliği vardır:

```xml
<deploymentProvider codebase="http://myserver/myapp.application" />
```

Bu yol, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulamayı oluşturduğunda ayarlanır ve yüklü uygulamalar için zorunlu olur. Yol, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] yükleyicinin uygulamayı yükleyeceğini ve güncelleştirmelerin aranacağı standart konuma işaret eder. Bir uygulamayı farklı bir konuma kopyalamak için **xcopy** komutunu kullanırsanız [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] , ancak özelliğini değiştirmeyin, `deploymentProvider` [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulamayı indirmeyi denediğinde yine de özgün konuma geri başvuracaktır.

Bir uygulamayı taşımak veya kopyalamak isterseniz, `deploymentProvider` istemcinin gerçekten yeni konumdan yüklemesi için yolu da güncelleştirmeniz gerekir. Uygulama yüklediyseniz, bu yolu güncelleştirme genellikle bir konudur. Özgün URL aracılığıyla her zaman başlatılan çevrimiçi uygulamalar için, ayarı `deploymentProvider` isteğe bağlıdır. `deploymentProvider`Ayarlanırsa, kabul edilir; Aksi takdirde, uygulamayı başlatmak için kullanılan URL, uygulama dosyalarını indirmek için temel URL olarak kullanılacaktır.

> [!NOTE]
> Bildirimi her güncelleştirdiğinizde yeniden imzalamanız da gerekir.

## <a name="see-also"></a>Ayrıca bkz.

[ClickOnce dağıtımları](../deployment/troubleshooting-clickonce-deployments.md) 
 sorunlarını giderme [Güvenli ClickOnce uygulamaları](../deployment/securing-clickonce-applications.md) 
 [ClickOnce dağıtım stratejisi seçin](../deployment/choosing-a-clickonce-deployment-strategy.md)
