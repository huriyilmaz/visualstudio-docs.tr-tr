---
title: ClickOnce uygulamaları için istemci bilgisayara güvenilir yayımcı ekleme
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, install without prompting
- trusted application deployment, Trusted Publishers
ms.assetid: 35fe324c-45a1-4509-b7be-5c18b4b1b4ab
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1423952405a31063ee88ce6fa1dfe0b75d80fe5d
ms.sourcegitcommit: ade07bd1cf69b8b494d171ae648cfdd54f7800d3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81649211"
---
# <a name="how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications"></a>Nasıl yapIlir: ClickOnce uygulamaları için istemci bilgisayara güvenilir bir yayımcı ekleme
Güvenilir Uygulama Dağıtımı ile istemci bilgisayarları, uygulamalarınızın [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] kullanıcıyı sormadan daha yüksek bir güven düzeyiyle çalışacak şekilde yapılandırabilirsiniz. Aşağıdaki yordamlar, istemci bilgisayardaki Güvenilir Yayımcılar deposuna yayımcı sertifikası eklemek için CertMgr.exe komut satırı aracının nasıl kullanılacağını gösterir.

 Kullandığınız komutlar, sertifikanızı veren sertifika yetkilisinin (CA) istemcinin güvenilen kökünün bir parçası olup olmadığına bağlı olarak biraz değişir. Bir Windows istemci bilgisayarı bir etki alanının parçasıysa, bir listede güvenilir kökler olarak kabul edilen CA'ları içerir. Bu liste genellikle sistem yöneticisi tarafından yapılandırılır. Sertifikanız bu güvenilen köklerden biri veya bu güvenilen köklerden birine zincirleyen bir CA tarafından verilmişse, sertifikayı istemcinin güvenilen kök deposuna ekleyebilirsiniz. Diğer taraftan, sertifikanız bu güvenilen köklerden biri tarafından verilmediyse, sertifikayı hem istemcinin Güvenilen Kök deposuna hem de Güvenilen Yayımcı deposuna eklemeniz gerekir.

> [!NOTE]
> Yüksek izinler gerektiren bir [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulama dağıtmayı planladığınız her istemci bilgisayara bu şekilde sertifika eklemeniz gerekir. Sertifikaları el ile veya müşterilerinize dağıttığınız bir uygulama aracılığıyla eklersiniz. Bu bilgisayarları yalnızca bir kez yapılandırmanız gerekir ve [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] ardından aynı sertifikayla imzalanmış herhangi bir sayıda uygulama dağıtabilirsiniz.

 Ayrıca, sınıfı kullanarak programlı bir şekilde <xref:System.Security.Cryptography.X509Certificates.X509Store> bir mağazaya sertifika ekleyebilirsiniz.

 Güvenilen Uygulama Dağıtımına genel [bakış](../deployment/trusted-application-deployment-overview.md)için bkz.

### <a name="to-add-a-certificate-to-the-trusted-publishers-store-under-the-trusted-root"></a>Güvenilen Yayımcılar deposuna güvenilen kök altında sertifika eklemek için

1. CA'dan dijital sertifika edinin.

2. Sertifikayı Base64 X.509 (*.cer*) biçimine aktarın. Sertifika biçimleri hakkında daha fazla bilgi için [bkz.](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc730988(v=ws.10))

3. İstemci bilgisayarlardaki komut isteminden aşağıdaki komutu çalıştırın:

     **certmgr.exe -add certificate.cer -c -s -r localMachine TrustedPublisher**

### <a name="to-add-a-certificate-to-the-trusted-publishers-store-under-a-different-root"></a>Güvenilen Yayımcılar mağazasına farklı bir kök altında sertifika eklemek için

1. CA'dan dijital sertifika edinin.

2. Sertifikayı Base64 X.509 (*.cer*) biçimine aktarın. Sertifika biçimleri hakkında daha fazla bilgi için [bkz.](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc730988(v=ws.10))

3. İstemci bilgisayarlardaki komut isteminden aşağıdaki komutu çalıştırın:

     **certmgr.exe -ekle good.cer -c -s -r localMachine Root**

     **certmgr.exe -ekle good.cer -c -s -r localMachine TrustedPublisher**

## <a name="see-also"></a>Ayrıca bkz.
- [İzlenecek yol: ClickOnce uygulamasını el ile dağıtma](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)
- [ClickOnce uygulamalarını koruma](../deployment/securing-clickonce-applications.md)
- [ClickOnce uygulamaları için kod erişimi güvenliği](../deployment/code-access-security-for-clickonce-applications.md)
- [ClickOnce ve Authenticode](../deployment/clickonce-and-authenticode.md)
- [Güvenilir uygulama dağıtımına genel bakış](../deployment/trusted-application-deployment-overview.md)
- [Nasıl Yapılır: ClickOnce güvenlik ayarlarını etkinleştirin](../deployment/how-to-enable-clickonce-security-settings.md)
- [Nasıl yapilir: ClickOnce uygulaması için bir güvenlik bölgesi ayarlama](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)
- [Nasıl yapılsın: ClickOnce uygulaması için özel izinleri ayarlama](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)
- [Nasıl?](securing-clickonce-applications.md)
- [Nasıl yapIlir: ClickOnce uygulamaları için istemci bilgisayara güvenilir bir yayımcı ekleme](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md)
- [Nasıl yapilir: Uygulama ve dağıtım bildirimlerini yeniden imzalama](../deployment/how-to-re-sign-application-and-deployment-manifests.md)
- [Nasıl yapılandırılır: ClickOnce güven istemi davranışını yapılandırın](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md)