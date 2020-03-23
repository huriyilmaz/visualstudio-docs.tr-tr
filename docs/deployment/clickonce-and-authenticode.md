---
title: ClickOnce ve Authenticode | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- .pfx files
- ClickOnce deployment, Authenticode
- Authenticode, ClickOnce
- ClickOnce deployment, certificates
- ClickOnce deployment, security
ms.assetid: ab5b6712-f32a-4e33-842f-e88ab4818ccf
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b9b0e22f56ab68be521eda7a765a2be7e23bbf92
ms.sourcegitcommit: 6c3aa85ff17916936018d121e7a0d1b486f6c7eb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/11/2020
ms.locfileid: "79093955"
---
# <a name="clickonce-and-authenticode"></a>ClickOnce ve Authenticode
*Authenticode,* uygulama yayımcısının orijinalliğini doğrulayan dijital sertifikalarla uygulama kodunu imzalamak için endüstri standardı şifreleme kullanan bir Microsoft teknolojisidir. Uygulama dağıtımı için Authenticode [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] kullanarak, bir Truva atı riskini azaltır. Truva atı, kötü niyetli bir üçüncü tarafın kurulmuş, güvenilir bir kaynaktan gelen meşru bir program olarak yanlış temsil ettiği bir virüs veya diğer zararlı programdır. Dağıtımları dijital sertifikayla imzalamak, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] derlemelerin ve dosyaların değiştirilmediğini doğrulamak için isteğe bağlı bir adımdır.

 Aşağıdaki bölümlerde Authenticode'da kullanılan farklı dijital sertifika türleri, Sertifika Yetkilileri (CA) kullanılarak sertifikaların nasıl doğrulanması, sertifikalarda zaman damgalamanın rolü ve Sertifika.

## <a name="authenticode-and-code-signing"></a>Authenticode ve kod imzalama
 *Dijital sertifika,* sertifikanın verildiği yayımcıyı ve sertifikayı veren ajansı açıklayan meta verilerle birlikte şifreleme genel/özel anahtar çifti içeren bir dosyadır.

 Çeşitli Authenticode sertifikaları vardır. Her biri farklı imza türleri için yapılandırılır. Uygulamalar [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] için, kod imzalama için geçerli bir Authenticode sertifikasına sahip olmalısınız. Bir [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulamayı dijital e-posta sertifikası gibi başka bir sertifika türüyle imzalamaya çalışırsanız, bu uygulama çalışmaz. Daha fazla bilgi için [kod imzalamaya giriş 'e](/windows/desktop/seccrypto/cryptography-tools)bakın.

 Kod imzalama sertifikasını üç şekilde elde edebilirsiniz:

- Sertifika satıcısından satın alın.

- Kuruluşunuzdaki dijital sertifikalar oluşturmaktan sorumlu bir gruptan bir tane alın.

- New-SelfSignedCertificate PowerShell cmdlet kullanarak veya *MakeCert.exe*kullanarak kendi sertifikanızı oluşturun [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)].

### <a name="how-using-certificate-authorities-helps-users"></a>Sertifika yetkililerinin kullanılması kullanıcılara nasıl yardımcı olur?
 New-SelfSignedCertificate veya *MakeCert.exe* yardımcı programı kullanılarak oluşturulan bir sertifika genellikle *kendi kendine sertifika* veya test *cert*denir. Bu tür bir sertifika *,snk* dosyasının .NET Framework'de çalıştığı gibi çalışır. Yalnızca genel/özel şifreleme anahtar çiftinden oluşur ve yayımcı hakkında doğrulanabilir hiçbir bilgi içermez. Bir intranet üzerinde yüksek güven [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] ile uygulamaları dağıtmak için kendi kendine sertifikaks kullanabilirsiniz. Ancak, bu uygulamalar istemci bilgisayarda [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] çalıştırıldığında, bunları Bilinmeyen Yayımcı'dan geldiğini tanımlar. Varsayılan olarak, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] kendi kendine sertifikalarla imzalanan ve Internet üzerinden dağıtılan uygulamalar Güvenilir Uygulama Dağıtımı'ndan kullanamaz.

 Bunun aksine, sertifika satıcısı veya kuruluşunuzdaki bir departman gibi bir CA'dan sertifika alırsanız, sertifika kullanıcılarınız için daha fazla güvenlik sunar. İmzalanan yazılımın yayımcısını tanımlamaz, aynı zamanda imzalayan CA ile kontrol ederek bu kimliği doğrular. CA kök yetkisini değilse, Authenticode ayrıca CA'nın sertifika verme yetkisine sahip olduğunu doğrulamak için kök otoriteye "zincir" de verecektir. Daha fazla güvenlik için, mümkün olduğunda CA tarafından verilen bir sertifika kullanmanız gerekir.

 Self-certs oluşturma hakkında daha fazla bilgi için [bkz.](https://technet.microsoft.com/itpro/powershell/windows/pkiclient/new-selfsignedcertificate) [MakeCert](/windows/desktop/SecCrypto/makecert)

### <a name="timestamps"></a>Zaman damgaları
 Uygulamaları imzalamak [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] için kullanılan sertifikaların süresi, genellikle on iki ay olmak üzere belirli bir süre sonra sona erer. Uygulamaları sürekli olarak yeni sertifikalarla yeniden imzalama ihtiyacını gidermek [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] için zaman damgasını destekler. Bir başvuru zaman damgası ile imzalandığında, zaman damgasının geçerli olması koşuluyla, süresi sona erdikten sonra bile sertifikası kabul etmeye devam edecektir. Bu, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] süresi dolmuş sertifikalara, ancak geçerli zaman damgalarına sahip uygulamaların karşıdan yükleyip çalıştırılamasına olanak tanır. Ayrıca, süresi dolmuş sertifikalara sahip yüklü uygulamaların güncelleştirmeleri karşıdan yüklemeye ve yüklemeye devam etmesine de olanak tanır.

 Bir uygulama sunucusuna bir zaman damgası eklemek için bir zaman damgası sunucusu nun kullanılabilir olması gerekir. Zaman damgası sunucusu nun nasıl seçilen hakkında bilgi için [bkz.](../ide/how-to-sign-application-and-deployment-manifests.md)

### <a name="update-expired-certificates"></a>Süresi dolan sertifikaları güncelleştirme
 .NET Framework'ün önceki sürümlerinde, sertifikası süresi dolmuş bir uygulamanın güncelleştirilmesi, uygulamanın çalışmasının durmasına neden olabilir. Bu sorunu gidermek için aşağıdaki yöntemlerden birini kullanın:

- .NET Framework'u 2.0 SP1 veya daha sonra Windows XP sürümünde veya 3.5 veya daha sonra Windows Vista sürümünde güncelleştirin.

- Uygulamayı kaldırın ve geçerli bir sertifikayla yeni bir sürümü yeniden yükleyin.

### <a name="store-certificates"></a>Mağaza sertifikaları

- Sertifikaları dosya sisteminizde *.pfx* dosyası olarak depolayabilir veya önemli bir kapsayıcının içinde saklayabilirsiniz. Windows etki alanında bir kullanıcı anahtar kapsayıcıları bir dizi olabilir. Varsayılan olarak, *MakeCert.exe* sertifikalarını kişisel anahtar kapsayıcınızda saklar, bunun yerine bir *.pfx'e* kaydetmesi gerektiğini belirtmediğiniz sürece. *Mage.exe* ve *MageUI.exe,* dağıtımlar oluşturmak [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] için araçlar, her iki moda saklanan sertifikaları kullanmanıza olanak sağlar.

## <a name="see-also"></a>Ayrıca bkz.
- [ClickOnce güvenlik ve dağıtım](../deployment/clickonce-security-and-deployment.md)
- [ClickOnce uygulamalarını koruma](../deployment/securing-clickonce-applications.md)
- [Güvenilir uygulama dağıtımına genel bakış](../deployment/trusted-application-deployment-overview.md)
- [Mage.exe (Bildirim Oluşturma ve Düzenleme Aracı)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)
