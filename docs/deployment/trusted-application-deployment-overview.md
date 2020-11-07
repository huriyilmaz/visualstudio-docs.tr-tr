---
title: Güvenilen uygulama dağıtımına genel bakış | Microsoft Docs
description: Güvenilen uygulama dağıtım teknolojisini kullanarak yükseltilmiş izinlere sahip ClickOnce uygulamalarını dağıtmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, install without prompting
- ClickOnce deployment, security
- trusted application deployment
ms.assetid: b24a1702-8fbe-45b1-87a0-9618a0708f1d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 96dfb98b468782f771d866b33b94b2c18de6276f
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94350510"
---
# <a name="trusted-application-deployment-overview"></a>Güvenilen uygulama dağıtımına genel bakış
Bu konu [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] , güvenilen uygulama dağıtım teknolojisini kullanarak yükseltilmiş izinlere sahip uygulamaların nasıl dağıtılacağı hakkında genel bakış sağlar.

 Dağıtım teknolojisinin bir parçası olan güvenilir uygulama dağıtımı [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] , her boyuttaki kuruluşların daha güvenli ve Kullanıcı istenmeden daha güvenli bir şekilde bir yönetilen uygulamaya ek izinler vermesini kolaylaştırır. Güvenilen uygulama dağıtımı sayesinde bir kuruluş, bir istemci bilgisayarı, Authenticode sertifikaları kullanılarak tanımlanan, güvenilen yayımcılar listesine sahip olacak şekilde yapılandırabilir. Bundan sonra, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Bu güvenilir yayımcıların biri tarafından imzalanan tüm uygulamalar daha yüksek bir güven düzeyi alır.

> [!NOTE]
> Güvenilen uygulama dağıtımı, bir kullanıcının bilgisayarında bir kerelik yapılandırma gerektirir. Yönetilen masaüstü ortamlarında, bu yapılandırma genel ilke kullanılarak gerçekleştirilebilir. Uygulamanız için istediğiniz bu değilse, bunun yerine izin yükseltme kullanın. Daha fazla bilgi için bkz. [ClickOnce uygulamalarının güvenliğini sağlama](../deployment/securing-clickonce-applications.md).

## <a name="trusted-application-deployment-basics"></a>Güvenilen uygulama dağıtımı temelleri
 Aşağıdaki tabloda, güvenilir uygulama dağıtımında yer alan nesneler ve roller gösterilmektedir.

|Nesne veya rol|Description|
|--------------------|-----------------|
|yönetici|İstemci bilgisayarlarını güncelleştirmeden ve korumadan sorumlu kuruluş varlığı|
|güven Yöneticisi|Ortak dil çalışma zamanı (CLR) içindeki, istemci uygulama güvenliğini zormaktan sorumlu alt sistem.|
|yayımcı|Uygulamayı yazan ve tutan varlık.|
|Dağıtıcı|Uygulamayı paketleyen ve kullanıcılara dağıtan varlık.|
|sertifika|Ortak ve özel anahtardan oluşan bir şifreleme imzası; Genel olarak, bir sertifika yetkilisi (CA) tarafından, kendi orijinalliğini yoklanarak verilir.|
|Authenticode sertifikası|Diğer şeyler arasında, sertifikanın hangi kullanımlar için kullanıldığını açıklayan gömülü meta veriler içeren bir sertifika.|
|sertifika yetkilisi|Yayımcıların kimliğini doğrulayan ve yayımcının meta verileriyle gömülü sertifikaları veren bir kuruluş.|
|kök yetkili|Sertifika vermek için diğer sertifika yetkililerine yetki veren bir sertifika yetkilisi.|
|anahtar kapsayıcısı|Sertifikaları depolamak için Microsoft Windows 'da mantıksal depolama alanı.|
|Güvenilen Yayımcı|Bir istemci bilgisayarda bir sertifika güven listesine (CTL) eklenen Authenticode sertifikası olan yayımcı.|

 Daha büyük kuruluşlarda, yayımcı ve dağıtıcı genellikle iki ayrı varlıklardır:

- Yayımcı, uygulamayı oluşturan gruptur [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] .

- Dağıtıcı, genellikle [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Şirket Kurumsal Masaüstü bilgisayarlara uygulamayı dağıtan, genellikle bilgi teknolojisi (BT) departmanı olan gruptur.

Güvenilen uygulama dağıtımının avantajlarından yararlanmak için aşağıdaki adımları izlemeniz gerekir:

1. Yayımcı için bir sertifika edinin.

2. Yayımcıyı tüm istemcilerde Güvenilen Yayımcılar deposuna ekleyin.

3. Uygulamanızı oluşturun [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] .

4. Dağıtım bildirimini yayımcının sertifikasıyla imzalayın.

5. Uygulama dağıtımını istemci bilgisayarlara yayımlayın.

### <a name="obtain-a-certificate-for-the-publisher"></a>Yayımcı için bir sertifika edinme
 Dijital sertifikalar, Microsoft Authenticode kimlik doğrulaması ve güvenlik sisteminin temel bir bileşenidir. Authenticode, Windows işletim sisteminin standart bir parçasıdır. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]Güvenilen uygulama dağıtımına katılıp katılmadığına bakılmaksızın tüm uygulamaların dijital sertifikayla imzalanması gerekir. Authenticode 'un ile nasıl çalıştığı hakkında tam bir açıklama için [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] bkz. [ClickOnce and Authenticode](../deployment/clickonce-and-authenticode.md).

### <a name="add-the-publisher-to-the-trusted-publishers-store"></a>Yayımcıyı Güvenilen Yayımcılar deposuna ekleme
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]Uygulamanızın daha yüksek bir güven düzeyi alması için, sertifikanızı Uygulamanın çalıştırılacağı her bir istemci bilgisayara güvenilir bir yayımcı olarak eklemeniz gerekir. Bu görevi gerçekleştirmek tek seferlik bir yapılandırmadır. İşlem tamamlandıktan sonra, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] istediğiniz gibi yayımcının sertifikasıyla imzalanmış sayıda uygulama dağıtabilir ve hepsi yüksek güvenle çalışır.

 Uygulamanızı yönetilen masaüstü ortamında dağıtıyorsanız; Örneğin, Windows işletim sistemini çalıştıran bir kurumsal intranet; grup ilkesi ile yeni bir sertifika güven listesi (CTL) oluşturarak, bir istemcinin deposuna güvenilen yayımcılar ekleyebilirsiniz. Daha fazla bilgi için, bkz. [Grup İlkesi bir nesne için sertifika güven listesi oluşturma](/previous-versions/windows/it-pro/windows-server-2003/cc728449(v=ws.10)).

 Uygulamanızı yönetilen bir masaüstü ortamında dağıtmaktan, güvenilen yayımcı deposuna bir sertifika eklemek için aşağıdaki seçeneklere sahip olursunuz:

- <xref:System.Security.Cryptography?displayProperty=fullName>Ad alanı.

- Internet Explorer 'ın bir bileşeni olan ve bu nedenle Windows 98 ve sonraki sürümlerde bulunan *CertMgr.exe*. Daha fazla bilgi için bkz. [Certmgr.exe (Sertifika Yöneticisi aracı)](/dotnet/framework/tools/certmgr-exe-certificate-manager-tool).

### <a name="create-a-clickonce-application"></a>ClickOnce uygulaması oluşturma
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]Uygulama, uygulamayı tanımlayan ve yükleme parametrelerini sağlayan bildirim dosyalarıyla birleştirilmiş bir .NET Framework istemci uygulamasıdır. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]Içindeki **Yayımla** komutunu kullanarak programınızı bir uygulamaya dönüştürebilirsiniz [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Alternatif olarak, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] içinde bulunan araçları kullanarak dağıtım için gerekli tüm dosyaları oluşturabilirsiniz [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)] . Dağıtım hakkında ayrıntılı adımlar için [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] bkz. [izlenecek yol: ClickOnce uygulamasını el ile dağıtma](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).

 Güvenilen uygulama dağıtımı öğesine özeldir [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] ve yalnızca uygulamalarla birlikte kullanılabilir [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] .

### <a name="sign-the-deployment"></a>Dağıtımı imzala
 Sertifikanızı aldıktan sonra dağıtımınızı imzalamak için onu kullanmanız gerekir. Uygulamanızı Yayımlama Sihirbazı 'nı kullanarak dağıtıyorsanız [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , sizin için bir sertifika belirtmediğinizde sihirbaz sizin için otomatik olarak bir test sertifikası oluşturacaktır. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]Bununla birlikte, BIR CA tarafından sağlanmış bir sertifika sağlamak için proje Tasarımcısı penceresini de kullanabilirsiniz.  Ayrıca bkz. [nasıl yapılır: yayımlama sihirbazını kullanarak ClickOnce uygulaması yayımlama](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).

> [!CAUTION]
> Uygulamanın bir test sertifikası ile dağıtılmasını önermiyoruz.

 *Mage.exe* veya *MageUI.exe* SDK araçlarını kullanarak da uygulamayı imzalayabilirsiniz. Daha fazla bilgi için bkz. [Izlenecek yol: ClickOnce uygulamasını el ile dağıtma](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Dağıtım imzalama ile ilgili komut satırı seçeneklerinin tam listesi için bkz. [Mage.exe (bildirim oluşturma ve düzenleme aracı)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool).

### <a name="publish-the-application"></a>Uygulamayı yayımlama
 Bildirimlerinizi imzaladıktan hemen sonra [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulama, yüklemenin konumuna yayımlamaya hazırız. Yükleme konumu bir Web sunucusu, bir dosya paylaşma veya yerel disk olabilir. İstemci dağıtım bildirimine ilk kez eriştiğinde güven Yöneticisi, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulamanın yetkili olarak verildiğini veya yüklü bir güvenilen yayımcı tarafından daha yüksek bir güven düzeyinde çalıştırılmadığını seçmesi gerekir. Güven Yöneticisi, dağıtımı imzalamak için kullanılan sertifikayı istemcinin güvenilen yayımcı deposunda depolanan sertifikalarla karşılaştırarak bu seçeneği tercih yapar. Güven Yöneticisi bir eşleşme bulursa, uygulama yüksek güvenle çalışır.

## <a name="trusted-application-deployment-and-permission-elevation"></a>Güvenilen uygulama dağıtımı ve Izin yükseltme
 Geçerli yayımcı güvenilen bir yayımcı değilse, güven Yöneticisi, uygulamanın yükseltilmiş izinlere izin verip vermediği hakkında kullanıcıyı sorgulamak için Izin yükseltmeyi kullanır. İzin yükseltme, yönetici tarafından devre dışı bırakılmışsa, uygulama çalıştırmak için izin alamaz. Uygulama çalıştırılmaz ve kullanıcıya hiçbir bildirim gösterilmez. Izin yükseltme hakkında daha fazla bilgi için bkz. [ClickOnce uygulamalarının güvenliğini sağlama](../deployment/securing-clickonce-applications.md).

## <a name="limitations-of-trusted-application-deployment"></a>Güvenilen uygulama dağıtımının sınırlamaları
 Güvenilen uygulama dağıtımını, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Web üzerinde dağıtılan uygulamalara veya bir kurumsal dosya paylaşımından yükseltilmiş güven sağlamak için kullanabilirsiniz. Bir CD üzerinde dağıtılan uygulamalar için güvenilir uygulama dağıtımı kullanmanız gerekmez [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] , çünkü varsayılan olarak bu uygulamalara tam güven verilir.

## <a name="see-also"></a>Ayrıca bkz.
- [Mage.exe (Bildirim Oluşturma ve Düzenleme Aracı)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)
- [İzlenecek yol: ClickOnce uygulamasını el ile dağıtma](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)
