---
title: ClickOnce ve Authenticode | Microsoft Docs
description: Authenticode'ın uygulamaların orijinalliğini doğrulamak için kullandığı sertifikalar hakkında bilgi öğrenin. Sertifikaların nasıl doğrulandığı ve depolandığı hakkında bilgi.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: e10c5281222e7c53410502867faa16d567d0bf4f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122133659"
---
# <a name="clickonce-and-authenticode"></a>ClickOnce ve Authenticode
*Authenticode,* uygulama kodunu uygulama yayımcılarının orijinalliğini doğru kullanan dijital sertifikalarla imzalamak için endüstri standardı şifreleme kullanan bir Microsoft teknolojisidir. Uygulama dağıtımı için Authenticode'ı kullanarak [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Truva atı riskini azaltır. Truva atı, kötü amaçlı bir üçüncü taraf tarafından kurulan ve güvenilir bir kaynaktan gelen meşru bir program olarak yanlış beyanda bulunduran bir virüs veya diğer zararlı programdır. Dağıtımları dijital sertifikayla imzalamak, derlemelerin ve dosyaların kurcalanmadığını doğrulamak [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] için isteğe bağlı bir adımdır.

 Aşağıdaki bölümlerde Authenticode'da kullanılan farklı dijital sertifika türleri, sertifikaların Sertifika Yetkilileri (CA) kullanılarak nasıl doğrulanması, sertifikalarda zaman damgasının rolü ve sertifikalar için kullanılabilir depolama yöntemleri açıklanmaktadır.

## <a name="authenticode-and-code-signing"></a>Kimlik doğrulama ve kod imzalama
 Dijital *sertifika,* bir şifreleme ortak/özel anahtar çifti içeren bir dosyanın yanı sıra sertifikanın yayımını yaptığı yayımcıyı ve sertifikayı yayımya alan kuruluşu açıklayan meta verilerdir.

 Çeşitli Authenticode sertifikası türleri vardır. Her biri farklı imzalama türleri için yapılandırılır. Uygulamalar [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] için, kod imzalama için geçerli bir Authenticode sertifikanız olmalıdır. Bir uygulamayı dijital e-posta sertifikası gibi başka bir sertifika türüyle imzalamaya [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] çalışırsanız uygulama çalışmayacaktır. Daha fazla bilgi için [bkz. Kod imzalamaya giriş.](/windows/desktop/seccrypto/cryptography-tools)

 Kod imzalama için üç farklı şekilde sertifika edinebilirsiniz:

- Sertifika satıcısından bir tane satın alın.

- Dijital sertifika oluşturmaktan sorumlu kuruluşta bir gruptan bir tane alırsınız.

- New-SelfSignedCertificate PowerShell cmdlet'ini kullanarak veya ile birlikte *MakeCert.exe* kullanarak kendi sertifikanızı [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)] oluşturma.

### <a name="how-using-certificate-authorities-helps-users"></a>Sertifika yetkililerini kullanmanın kullanıcılara nasıl yardımcı olduğu
 New-SelfSignedCertificate veyaMakeCert.exekullanılarak oluşturulan sertifika  genellikle kendi kendine sertifika veya  test sertifikası olarak *da adlandırılan bir sertifikadır.* Bu tür bir sertifika, bir *.snk* dosyasının dosya dosyasındaki çalışma .NET Framework. Yalnızca ortak/özel bir şifreleme anahtarı çifti içerir ve yayımcı hakkında doğrulanabilir bilgi içerir. İntranet üzerinde yüksek güvene sahip uygulamalar [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dağıtmak için kendi kendine sertifikalar kullanabilirsiniz. Ancak, bu uygulamalar bir istemci bilgisayarda çalıştır olduğunda, bilinmeyen bir bilgisayardan [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] geliyor Publisher. Varsayılan olarak, kendi kendine sertifikalarla imzalanan ve İnternet üzerinden dağıtılan uygulamalar [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Güvenilen Uygulama Dağıtımı'nın kullanılamayacak.

 Buna karşılık, sertifika satıcısı gibi bir CA'dan veya kuruluş içindeki bir departmandan sertifika alırsanız, sertifika kullanıcılarınız için daha fazla güvenlik sunar. İmzalı yazılımın yayımcılarını tanımlamanın yanında, onu imzalayan CA'ya bakarak bu kimliği doğrular. CA kök yetkilisi yoksa Authenticode, CA'nın sertifikalar sağlamak için yetkili olduğunu doğrulamak için kök yetkiliye "zincirle" döner. Daha fazla güvenlik için, mümkün olduğunda bir CA tarafından verilen bir sertifika kullanılmalıdır.

 Kendi kendine sertifika oluşturma hakkında daha fazla bilgi için bkz. [New-SelfSignedCertificate veya](/powershell/module/pkiclient/new-selfsignedcertificate) [MakeCert](/windows/desktop/SecCrypto/makecert).

### <a name="timestamps"></a>Zaman damgaları
 Uygulamaları imzalamak için kullanılan [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] sertifikaların süresi, genellikle on iki ay gibi belirli bir sürenin ardından dolar. Uygulamaları yeni sertifikalarla sürekli yeniden imzalama ihtiyacı ortadan kaldırmak için zaman [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] damgasını destekler. Bir uygulama bir zaman damgasıyla imzalanıyorsa, zaman damgası geçerli olması şartıyla, süresi dolsa bile sertifikası kabul edilmeye devam eder. Bu, süresi dolmuş sertifikalara ancak geçerli zaman damgasına sahip uygulamaların indirme [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] ve çalıştırmasını sağlar. Ayrıca, süresi dolmuş sertifikalara sahip yüklü uygulamaların güncelleştirmeleri indirmeye ve yüklemeye devam eder.

 Uygulama sunucusuna bir zaman damgası eklemek için zaman damgası sunucusunun kullanılabilir olması gerekir. Bir zaman damgası sunucusunu seçme hakkında bilgi için bkz. [Nasıl kullanılır: Uygulama ve Dağıtım Bildirimlerini İmzala.](../ide/how-to-sign-application-and-deployment-manifests.md)

### <a name="update-expired-certificates"></a>Süresi dolan sertifikaları güncelleştirme
 Uygulamanın önceki sürümlerinde.NET Framework süresi dolmuş bir uygulamanın güncelleştirilerek uygulamanın çalışmasının durdurmasına neden olabilir. Bu sorunu çözmek için aşağıdaki yöntemlerden birini kullanın:

- .NET Framework XP'de 2.0 SP1 veya sonraki bir sürüme veya Vista'da Windows 3.5 veya sonraki bir Windows güncelleştirin.

- Uygulamayı kaldırın ve geçerli bir sertifika ile yeni bir sürümü yeniden yükleyin.

### <a name="store-certificates"></a>Sertifikaları depolama

- Sertifikaları dosya sisteminize *bir .pfx* dosyası olarak depolar veya bunları bir anahtar kapsayıcının içinde depolar. Etki alanındaki Windows çok sayıda anahtar kapsayıcısı olabilir. Varsayılan *olarak,MakeCert.exe* kişisel anahtar kapsayıcınıza kaydetmesi gerektiğini belirtmedikçe sertifikalar kişisel anahtar kapsayıcınıza *depolar.* *Mage.exe* *veMageUI.exe,* dağıtım oluşturmaya yardımcı olan araçları kullanarak her iki [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] şekilde de depolanan sertifikaları [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] kullanabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.
- [ClickOnce güvenliği ve dağıtımı](../deployment/clickonce-security-and-deployment.md)
- [ClickOnce uygulamalarını koruma](../deployment/securing-clickonce-applications.md)
- [Güvenilir uygulama dağıtımına genel bakış](../deployment/trusted-application-deployment-overview.md)
- [Mage.exe (Bildirim Oluşturma ve Düzenleme Aracı)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)