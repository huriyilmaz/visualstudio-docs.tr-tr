---
title: ClickOnce ve Authenticode | Microsoft Docs
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
ms.openlocfilehash: ed7945dac94527df51dcdd601113f8874cd36142
ms.sourcegitcommit: 1803a67b516f67b209d8f4cf147314e604ef1927
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2020
ms.locfileid: "89641627"
---
# <a name="clickonce-and-authenticode"></a>ClickOnce ve Authenticode
*Authenticode* , uygulama kodunu uygulama yayımcısının orijinalliğini doğrulayan dijital sertifikalarla imzalamak için sektör standardı şifrelemeyi kullanan bir Microsoft teknolojisidir. Uygulama dağıtımı için Authenticode kullanarak [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] bir Truva atı riskini azaltır. Truva atı, kötü amaçlı üçüncü tarafın oluşturulmuş, güvenilir bir kaynaktan gelen yasal bir program olarak yanlış temsil ettiği bir virüs veya diğer zararlı programdır. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]Dijital sertifikayla imzalama dağıtımları, derlemelerin ve dosyaların değiştirilmediğini doğrulamak için isteğe bağlı bir adımdır.

 Aşağıdaki bölümler, Authenticode 'da kullanılan farklı dijital sertifika türlerini, sertifika yetkilileri (CA 'Lar) kullanarak sertifikaların nasıl doğrulanacağını, sertifikalarda zaman damgalaması rolünü ve sertifikalar için kullanılabilen depolama yöntemlerini açıklamaktadır.

## <a name="authenticode-and-code-signing"></a>Authenticode ve kod imzalama
 *Dijital sertifika* , şifreli ortak/özel anahtar çifti içeren bir dosyadır ve sertifikanın verildiği yayımcıyı ve sertifikayı veren Kurumu tanımlayan meta verileri içerir.

 Çeşitli Authenticode sertifikası türleri vardır. Her biri farklı imzalama türleri için yapılandırılır. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]Uygulamalar için, kod imzalama için geçerli olan bir Authenticode sertifikasına sahip olmanız gerekir. Bir [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulamayı dijital e-posta sertifikası gibi başka bir sertifika türüyle imzalamayı denerseniz, bu işlem çalışmaz. Daha fazla bilgi için bkz. [kod Imzalamaya giriş](/windows/desktop/seccrypto/cryptography-tools).

 Kod imzalama için üç şekilde bir sertifika edinebilirsiniz:

- Bir sertifika satıcısından bir tane satın alın.

- Kuruluşunuzda dijital sertifikalar oluşturmaktan sorumlu bir gruptan bir tane alın.

- New-SelfSignedCertificate PowerShell cmdlet 'ini kullanarak veya ile birlikte bulunan *MakeCert.exe*kullanarak kendi sertifikanızı oluşturun [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)] .

### <a name="how-using-certificate-authorities-helps-users"></a>Sertifika yetkililerini kullanma, kullanıcılara yardımcı olur
 New-SelfSignedCertificate veya *MakeCert.exe* yardımcı programı kullanılarak oluşturulan bir sertifika, genellikle *kendi kendine sertifika* veya *test sertifikası*olarak adlandırılır. Bu tür bir sertifika, bir *. snk* dosyası .NET Framework çalıştığı şekilde oldukça geçerlidir. Yalnızca ortak/özel bir şifreleme anahtarı çiftinin oluşur ve yayımcı hakkında doğrulanabilir bilgiler içermez. Self-cert kullanarak, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] bir intranette yüksek güvenle uygulama dağıtabilirsiniz. Ancak, bu uygulamalar bir istemci bilgisayarında çalıştırıldığında, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] bunları bilinmeyen bir yayımcıdan geldiği şekilde tanımlayacaktır. Varsayılan olarak, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] self-cert ile imzalanmış ve Internet üzerinden dağıtılan uygulamalar, güvenilir uygulama dağıtımını kullanamaz.

 Buna karşılık, sertifika satıcısı veya kuruluşunuzdaki bir departman gibi bir CA 'dan sertifika alırsanız, sertifika kullanıcılarınız için daha fazla güvenlik sağlar. Yalnızca imzalı yazılımın yayımcısını tanımlamaz, ancak onu imzalayan CA ile kontrol ederek kimliği doğrular. CA kök yetkili değilse, CA 'nın sertifika verme yetkisine sahip olduğunu doğrulamak için, Authenticode da kök yetkiliye geri gönderilir. Daha fazla güvenlik için, mümkün olduğunda CA tarafından verilen bir sertifika kullanmanız gerekir.

 Self-cert oluşturma hakkında daha fazla bilgi için, bkz. [New-SelfSignedCertificate](/powershell/module/pkiclient/new-selfsignedcertificate) veya [MakeCert](/windows/desktop/SecCrypto/makecert).

### <a name="timestamps"></a>Zaman damgaları
 Uygulamaları imzalamak için kullanılan sertifikalar [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] , genellikle on iki ay boyunca belirli bir süre sonra sona erer. Uygulamaları yeni sertifikalarla sürekli olarak yeniden imzalama gereksinimini ortadan kaldırmak için [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] zaman damgasını destekler. Bir uygulama bir zaman damgasıyla imzalanmışsa, zaman damgası geçerli olduğundan, sertifikanın süresi dolduktan sonra bile kabul edilmesine devam edilir. Bu [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] , zaman aşımına uğradı, ancak geçerli zaman damgalarına sahip uygulamaların indirilip çalıştırılmasını sağlar. Ayrıca, güncelleştirmeleri indirmeye ve yüklemeye devam etmek için, süre dolma sertifikaları olan yüklü uygulamalara da izin verir.

 Bir uygulama sunucusuna bir zaman damgası eklemek için, kullanılabilir bir zaman damgası sunucusu olmalıdır. Zaman damgası sunucusu seçme hakkında daha fazla bilgi için bkz. [nasıl yapılır: uygulama ve dağıtım bildirimlerini imzalama](../ide/how-to-sign-application-and-deployment-manifests.md).

### <a name="update-expired-certificates"></a>Süre dolma sertifikalarını Güncelleştir
 .NET Framework önceki sürümlerinde, sertifikasının geçerliliği aşıldığı bir uygulamanın güncelleştirilmesi uygulamanın çalışmayı durdurmasına neden olabilir. Bu sorunu çözmek için aşağıdaki yöntemlerden birini kullanın:

- Windows Vista 'da Windows XP veya sürüm 3,5 veya sonraki sürümlerde .NET Framework sürüm 2,0 SP1 veya sonraki bir sürüme güncelleştirin.

- Uygulamayı kaldırın ve geçerli bir sertifikayla yeni bir sürümü yeniden yükleyin.

### <a name="store-certificates"></a>Sertifikaları depola

- Sertifikaları dosya sisteminizde bir *. pfx* dosyası olarak saklayabilir veya bunları bir anahtar kapsayıcısının içine kaydedebilirsiniz. Windows etki alanındaki bir kullanıcının birçok anahtar kapsayıcısı olabilir. *MakeCert.exe* , varsayılan olarak, bunun yerine bir *. pfx* ' e kaydedilmesini belirtmediğiniz müddetçe, sertifikaları Kişisel anahtar kapsayıcıınızda depolayacaktır. *Mage.exe* ve *MageUI.exe*, [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] dağıtım oluşturmaya yönelik araçlar [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] , her iki şekilde depolanan sertifikaları kullanmanıza olanak sağlar.

## <a name="see-also"></a>Ayrıca bkz.
- [ClickOnce güvenliği ve dağıtımı](../deployment/clickonce-security-and-deployment.md)
- [ClickOnce uygulamalarını koruma](../deployment/securing-clickonce-applications.md)
- [Güvenilir uygulama dağıtımına genel bakış](../deployment/trusted-application-deployment-overview.md)
- [Mage.exe (Bildirim Oluşturma ve Düzenleme Aracı)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)