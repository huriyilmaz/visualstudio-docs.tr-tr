---
title: İstemci kutusuna güvenilir yayımcı ekleme (ClickOnce)
description: İstemci uygulamalarınızı kullanıcıya sormadan daha yüksek bir güven düzeyinde ClickOnce bir istemci bilgisayara sertifika eklemeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: 5005c64ba03b91a9150258e501e8ef07deac00ac
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122146413"
---
# <a name="how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications"></a>Nasıl kullanılır: İstemci uygulamaları için istemci bilgisayara güvenilir yayımcı ClickOnce ekleme
Güvenilen Uygulama Dağıtımı ile istemci bilgisayarları, uygulamalarınızı kullanıcıya sorulmadan daha yüksek bir güven [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] düzeyiyle çalıştıracak şekilde yapılandırabilirsiniz. Aşağıdaki yordamlar, bir yayımcının sertifikasını istemci CertMgr.exe Güvenilen Yayımcılar deposuna eklemek için komut satırı aracının nasıl kullanılası göstermektedir.

 Kullandığınız komutlar, sertifikanızı verilen sertifika yetkilisinin (CA) bir istemcinin güvenilen kökünün parçası olup olmadığınıza bağlı olarak biraz farklılık gösterir. İstemci Windows bir etki alanının parçası ise, güvenilir kök olarak kabul edilen SERTIFIKA'ları bir listede içerir. Bu liste genellikle sistem yöneticisi tarafından yapılandırılır. Sertifikanız bu güvenilen köklerden biri veya bu güvenilen köklerden birini zincire takan bir CA tarafından verildi ise, sertifikayı istemcinin güvenilen kök deposuna indirebilirsiniz. Öte yandan, sertifikanız bu güvenilen köklerden biri tarafından verilmiyorsa, sertifikayı hem istemcinin Güvenilen Kök deposuna hem de Güvenilen kök Publisher eklemeniz gerekir.

> [!NOTE]
> Yükseltilmiş izinler gerektiren bir uygulamayı dağıtmayı planlasanız her istemci bilgisayara bu [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] şekilde sertifikalar eklemeniz gerekir. Sertifikaları el ile veya istemcilerinize dağıtarak bir uygulama aracılığıyla eklersiniz. Bu bilgisayarları yalnızca bir kez yapılandırmanız gerekir. Daha sonra aynı sertifikayla imzalanan [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] herhangi bir sayıda uygulamayı dağıtabilirsiniz.

 Ayrıca sınıfını kullanarak bir depoya program aracılığıyla sertifika <xref:System.Security.Cryptography.X509Certificates.X509Store> indirebilirsiniz.

 Güvenilen Uygulama Dağıtımına genel bakış için bkz. Güvenilen uygulama [dağıtımına genel bakış.](../deployment/trusted-application-deployment-overview.md)

### <a name="to-add-a-certificate-to-the-trusted-publishers-store-under-the-trusted-root"></a>Güvenilen kök altındaki Güvenilen Yayımcılar deposuna sertifika eklemek için

1. CA'dan dijital sertifika alın.

2. Sertifikayı Base64 X.509 (*.cer*) biçiminde dışarı aktarın. Sertifika biçimleri hakkında daha fazla bilgi için [bkz. Sertifikayı dışarı aktarma.](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc730988(v=ws.10))

3. İstemci bilgisayarlardaki komut isteminde aşağıdaki komutu çalıştırın:

     **certmgr.exe -add certificate.cer -c -s -r localMachine TrustedPublisher**

### <a name="to-add-a-certificate-to-the-trusted-publishers-store-under-a-different-root"></a>Güvenilen Yayımcılar deposuna farklı bir kök altında sertifika eklemek için

1. CA'dan dijital sertifika alın.

2. Sertifikayı Base64 X.509 (*.cer*) biçiminde dışarı aktarın. Sertifika biçimleri hakkında daha fazla bilgi için bkz. [Sertifikayı Dışarı Aktarma.](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc730988(v=ws.10))

3. İstemci bilgisayarlardaki komut isteminde aşağıdaki komutu çalıştırın:

     **certmgr.exe -add good.cer -c -s -r localMachine Root**

     **certmgr.exe -add good.cer -c -s -r localMachine TrustedPublisher**

## <a name="see-also"></a>Ayrıca bkz.
- [İzlenecek yol: ClickOnce uygulamasını el ile dağıtma](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)
- [ClickOnce uygulamalarını koruma](../deployment/securing-clickonce-applications.md)
- [ClickOnce uygulamaları için kod erişimi güvenliği](../deployment/code-access-security-for-clickonce-applications.md)
- [ClickOnce ve Authenticode](../deployment/clickonce-and-authenticode.md)
- [Güvenilir uygulama dağıtımına genel bakış](../deployment/trusted-application-deployment-overview.md)
- [Nasıl yapabilirsiniz: ClickOnce ayarlarını etkinleştirme](../deployment/how-to-enable-clickonce-security-settings.md)
- [Nasıl ClickOnce uygulama için güvenlik bölgesi ayarlama](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)
- [Nasıl ClickOnce uygulama için özel izinler ayarlama](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)
- [Nasıl ClickOnce: Kısıtlanmış ClickOnce uygulamanın hata ayıklaması](securing-clickonce-applications.md)
- [Nasıl kullanılır: İstemci uygulamaları için istemci bilgisayara güvenilir yayımcı ClickOnce ekleme](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md)
- [Nasıl: Uygulama ve dağıtım bildirimlerini yeniden imzalama](../deployment/how-to-re-sign-application-and-deployment-manifests.md)
- [Nasıl yapılandırılır: ClickOnce istemi davranışını yapılandırma](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md)