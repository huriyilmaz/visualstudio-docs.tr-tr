---
title: 'Nasıl yapılır: ClickOnce uygulamaları için bir Istemci bilgisayara güvenilir yayımcı ekleme | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, install without prompting
- trusted application deployment, Trusted Publishers
ms.assetid: 35fe324c-45a1-4509-b7be-5c18b4b1b4ab
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 296aec3b2b5cd307400b230375a7171f158fee60
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75847690"
---
# <a name="how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications"></a>Nasıl yapılır: ClickOnce Uygulamaları için Sunucu Bilgisayara Güvenilir Yayımcı Ekleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Güvenilen uygulama dağıtımı ile, istemci bilgisayarlarını, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] uygulamalarınızın kullanıcıya sormadan daha yüksek bir güven düzeyiyle çalışması için yapılandırabilirsiniz. Aşağıdaki yordamlarda, bir istemci bilgisayarındaki Güvenilen Yayımcılar deposuna bir yayımcının sertifikasını eklemek için CertMgr. exe komut satırı aracının nasıl kullanılacağı gösterilmektedir.  
  
 Kullandığınız komutlar, sertifikanızı veren sertifika yetkilisinin (CA) bir istemcinin güvenilen kökünün parçası olmasına bağlı olarak biraz farklılık gösterir. Bir Windows istemci bilgisayarı bir etki alanının parçasıysa, bir listede, Güvenilen kökler olarak kabul edilen CA 'Lar bulunur. Bu liste genellikle sistem yöneticisi tarafından yapılandırılır. Sertifikanız bu güvenilir köklerin biri tarafından veya bu güvenilen köklerin birine zincirde olan bir CA tarafından verildiyse, sertifikayı istemcinin güvenilen kök deposuna ekleyebilirsiniz. Diğer taraftan, sertifikanız bu güvenilir köklerin biri tarafından verilmiyorsa, sertifikayı hem istemcinin güvenilen kök deposuna hem de güvenilen yayımcı deposuna eklemeniz gerekir.  
  
> [!NOTE]
> Bu şekilde, yükseltilmiş izinler gerektiren bir [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] uygulaması dağıtmayı planladığınız her istemci bilgisayara sertifika eklemeniz gerekir. Sertifikaları el ile veya istemcilerinize dağıttığınız bir uygulama aracılığıyla eklersiniz. Bu bilgisayarları yalnızca bir kez yapılandırmanız gerekir, bundan sonra aynı sertifikayla imzalanmış istediğiniz sayıda [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] uygulamayı dağıtabilirsiniz.  
  
 Ayrıca, <xref:System.Security.Cryptography.X509Certificates.X509Store> sınıfını kullanarak programlı bir sertifikayı bir depoya ekleyebilirsiniz.  
  
 Güvenilen uygulama dağıtımına genel bakış için bkz. [Güvenilen uygulama dağıtımına genel bakış](../deployment/trusted-application-deployment-overview.md).  
  
### <a name="to-add-a-certificate-to-the-trusted-publishers-store-under-the-trusted-root"></a>Güvenilen bir kök altında Güvenilen Yayımcılar deposuna bir sertifika eklemek için  
  
1. Bir CA 'dan dijital sertifika alın.  
  
2. Sertifikayı Base64 X. 509.440 (. cer) biçiminde dışarı aktarın. Sertifika biçimleri hakkında daha fazla bilgi için bkz. [bir sertifikayı dışarı aktarma](https://technet.microsoft.com/library/cc730988(WS.10).aspx).  
  
3. İstemci bilgisayarlardaki komut isteminden aşağıdaki komutu çalıştırın:  
  
     **certmgr. exe-sertifika ekleme. cer-c-s-r localMachine TrustedPublisher**  
  
### <a name="to-add-a-certificate-to-the-trusted-publishers-store-under-a-different-root"></a>Farklı bir kök altında Güvenilen Yayımcılar deposuna bir sertifika eklemek için  
  
1. Bir CA 'dan dijital sertifika alın.  
  
2. Sertifikayı Base64 X. 509.440 (. cer) biçiminde dışarı aktarın. Sertifika biçimleri hakkında daha fazla bilgi için bkz. [bir sertifikayı dışarı aktarma](https://technet.microsoft.com/library/cc730988(WS.10).aspx).  
  
3. İstemci bilgisayarlardaki komut isteminden aşağıdaki komutu çalıştırın:  
  
     **certmgr. exe-iyi. cer-c-s-r localMachine kökünü ekleyin**  
  
     **certmgr. exe-iyi. cer-c-s-r localMachine TrustedPublisher ekleyin**  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Izlenecek yol: ClickOnce uygulamasını El Ile dağıtma](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)   
 [ClickOnce uygulamalarının güvenliğini sağlama](../deployment/securing-clickonce-applications.md)   
 [ClickOnce uygulamaları Için kod erişimi güvenliği](../deployment/code-access-security-for-clickonce-applications.md)   
 [ClickOnce ve Authenticode](../deployment/clickonce-and-authenticode.md)   
 [Güvenilen uygulama dağıtımına genel bakış](../deployment/trusted-application-deployment-overview.md)   
 [Nasıl yapılır: ClickOnce güvenlik ayarlarını etkinleştirme](../deployment/how-to-enable-clickonce-security-settings.md)   
 [Nasıl yapılır: ClickOnce uygulaması Için güvenlik bölgesi ayarlama](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)   
 [Nasıl yapılır: ClickOnce uygulaması Için özel Izinleri ayarlama](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)   
 [Nasıl yapılır: kısıtlanmış Izinlerle ClickOnce uygulamasında hata ayıklama](../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)   
 [Nasıl yapılır: ClickOnce uygulamaları için bir Istemci bilgisayara güvenilir yayımcı ekleme](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md)   
 [Nasıl yapılır: uygulama ve dağıtım bildirimlerini yeniden imzalama](../deployment/how-to-re-sign-application-and-deployment-manifests.md)   
 [Nasıl yapılır: ClickOnce Güven İstemi Davranışını Yapılandırma](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md)
