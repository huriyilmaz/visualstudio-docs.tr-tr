---
title: Diğer ClickOnce Dağıtan Uygulamalar Oluşturma | Microsoft Docs
description: .NET Framework 3.5 ve önceki sürümlerinde geliştirilen müşteri tarafından barındırılan ClickOnce uygulamaları hakkında bilgi .NET Framework.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- preserved branding information
- useManifestForTrust element
- customer deployments [ClickOnce]
- multiple ClickOnce deployment and branding
- ClickOnce applications, previous .NET Framework versions
- application manifests [ClickOnce]
- <useManifestForTrust> element
- manifests [ClickOnce]
- trust applications, ClickOnce
- ClickOnce applications, deployed by others
- ClickOnce applications, previous .NET Framework
ms.assetid: d20766c7-4ef3-45ab-8aa0-3f15b61eccaa
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: 4d917ff087005264510b512f0a028c5621e74f8a6f79ab80ac9b119d647a1cc8
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121404003"
---
# <a name="create-clickonce-applications-for-others-to-deploy"></a>Başkalarının dağıtması için ClickOnce uygulamaları oluşturma
Dağıtımlar oluşturmakta olan ClickOnce, uygulamaları kendileri dağıtmayı planlamaz. Bunların çoğu, uygulamayı yalnızca ClickOnce kullanarak paketlemektedir ve ardından dosyaları büyük bir şirket gibi bir müşteriye teslim ediyor. Müşteri, uygulamayı kendi ağına barındırmak için sorumlu olan kişi olur. Bu konu, sürüm 3.5'den önceki sürümlerde bu .NET Framework bazı sorunları ele almaktadır. Ardından, .NET Framework 3.5'te yeni "güven bildirimini kullan" özelliği kullanılarak sağlanan yeni .NET Framework açıklar. Son olarak, uygulamanın eski sürümlerini kullanmaya devam eden müşteriler için ClickOnce dağıtımları oluşturmak için önerilen stratejilerle .NET Framework.

## <a name="issues-involved-in-creating-deployments-for-customers"></a>Müşteriler için dağıtım oluşturmayla ilgili sorunlar
 Müşteriye dağıtım yapmayı planlamalısınız. İlk sorun kod imzalamayla ilgili. Bir ağ üzerinde dağıtılacak bir dağıtım bildirimi ve uygulama bildirimi ClickOnce bir dijital sertifika ile imzalandırmalısınız. Bu durum, bildirimleri imzalarken geliştiricinin sertifikasını mı yoksa müşterinin sertifikasını mı kullanabileceğini sorusunu ortaya çıkartır.

 Bir uygulamanın kimliği, dağıtım bildiriminin dijital imzasını temel ClickOnce için hangi sertifikanın kullanmalısınız sorusu kritik öneme sahip. Geliştirici dağıtım bildirimini imzalarsa, müşteri büyük bir şirketse ve şirketin birden fazla bölümü uygulamanın özelleştirilmiş bir sürümünü dağıtıyorsa çakışmalara neden olabilir.

 Örneğin Adventure Works'de bir finans departmanı ve insan kaynakları departmanı olduğunu söylemek gerekir. Her iki departman da ClickOnce veritabanında Microsoft Corporation rapor oluşturan bir uygulamanın lisansını SQL alır. Microsoft, her departmana verileri için özelleştirilmiş bir uygulama sürümü sağlar. Uygulamalar aynı Authenticode sertifikasıyla imzalandı ise, her iki uygulamayı da kullanmaya çalışan bir kullanıcı hatayla karşılaşır ve ClickOnce ikinci uygulamanın birinciyle aynı olduğunu kabul etmek zorunda olacaktır. Bu durumda müşteri, uygulama tarafından yerel olarak depolanan verilerin kaybını da içeren öngörülemeyen ve istenmeyen yan etkilere yol açabilir.

 Kod imzalamayla ilgili ek bir sorun, uygulama güncelleştirmelerinin nerede ClickOnce `deploymentProvider` dağıtım bildiriminde öğesidir. Bu öğe imzadan önce dağıtım bildirimine eklenmiştir. Bu öğe daha sonra eklenirse, dağıtım bildiriminin yeniden imza olması gerekir.

### <a name="require-the-customer-to-sign-the-deployment-manifest"></a>Müşterinin dağıtım bildirimini imzalamasını gerektirme
 Benzersiz olmayan dağıtımlar sorununun bir çözümü, geliştiricinin uygulama bildirimini imzalamasını ve müşterinin dağıtım bildirimini imzalamasını sağlamaktır. Bu yaklaşım işe yararken başka sorunlar da ortaya konur. Authenticode sertifikasının korumalı bir varlık olarak kalması gerekir, müşteri yalnızca geliştiriciye dağıtımı imzalaması için sertifikayı veremeyen bir varlıktır. Müşteri dağıtım bildirimini .NET Framework SDK'sı ile birlikte ücretsiz olarak kullanılabilir araçları kullanarak kendileri imzalasa da, bu durum müşterinin istekli veya sağyabilecekten daha fazla teknik bilgi gerektirir. Bu gibi durumlarda geliştirici genellikle bir uygulama, Web sitesi veya müşterinin imzalama için uygulama sürümünü gönderenin başka bir mekanizma oluşturur.

### <a name="the-impact-of-customer-signing-on-clickonce-application-security"></a>Müşterinin oturum açma etkisinin ClickOnce güvenliği
 Geliştirici ve müşteri, müşterinin uygulama bildirimini imzalaması gerektiğini kabul ediyor olsa bile, bu durum özellikle de güvenilen uygulama dağıtımı için geçerli olduğu için uygulamanın kimliğini çevreleyen başka sorunlar da ortaya çıkar. (Bu özellik hakkında daha fazla bilgi için bkz. [Güvenilen uygulama dağıtımına genel bakış.)](../deployment/trusted-application-deployment-overview.md) Adventure Works'in istemci bilgisayarlarını, bu uygulama tarafından sağlanan tüm Microsoft Corporation güvenerek yapılandırmak istediğini varsayın. Adventure Works dağıtım bildirimini imzalarsa ClickOnce uygulamanın güven düzeyini belirlemek için Adventure Work'in güvenlik imzasını kullanır.

## <a name="create-customer-deployments-by-using-application-manifest-for-trust"></a>Güven için uygulama bildirimini kullanarak müşteri dağıtımları oluşturma
 ClickOnce 3.5 .NET Framework, geliştiricilere ve müşterilere bildirimlerin nasıl imzalanacakları senaryosuna yeni bir çözüm veren yeni bir özellik içerir. Uygulama ClickOnce bildirimi, geliştiricinin uygulama bildiriminin dijital imzasını güven kararları vermek için kullanılacak şey olduğunu onaylamasını sağlayan adlı yeni `<useManifestForTrust>` bir öğeyi destekler. Geliştirici, bu öğeyi uygulama bildirimine dahil etmek ve hem *Mage.exe,* *MageUI.exe* ve Visual Studio gibi ClickOnce paketleme araçlarını hem kendi Publisher adını hem de uygulamanın adını bildirime eklemek için kullanır.

 kullanırken, `<useManifestForTrust>` dağıtım bildiriminin bir sertifika yetkilisi tarafından verilen bir Authenticode sertifikasıyla imzalandırmış olması gerekir. Bunun yerine, otomatik olarak imzalanan sertifika olarak bilinen ile imzalanmıştır. Otomatik olarak imzalanan sertifika müşteri veya geliştirici tarafından standart .NET Framework SDK araçları kullanılarak oluşturulur ve ardından standart ClickOnce dağıtım araçları kullanılarak dağıtım bildirimine uygulanır. Daha fazla bilgi için bkz. [MakeCert](/windows/desktop/SecCrypto/makecert).

 Dağıtım bildirimi için otomatik olarak imzalanan bir sertifika kullanmak çeşitli avantajlar sunar. Müşterinin kendi Authenticode sertifikasını alma veya oluşturma ihtiyacı ortadan kaldırarak, geliştiricinin uygulama üzerinde kendi marka kimliğini sürdürmesini sağlarken müşteri için dağıtımı `<useManifestForTrust>` kolaylaştırır. Sonuç, daha güvenli ve benzersiz uygulama kimlikleri olan imzalı dağıtımlar kümesidir. Bu, aynı uygulamayı birden çok müşteriye dağıtmanın olası çakışmalarını ortadan kaldırıyor.

 Etkin bir ClickOnce dağıtımı oluşturma hakkında adım adım bilgi için bkz. Kılavuz: Yeniden imzalama gerektirmeyen ve marka bilgilerini koruyan bir ClickOnce uygulamasını el `<useManifestForTrust>` [ile dağıtma.](../deployment/walkthrough-manually-deploying-a-clickonce-app-no-re-signing-required.md)

### <a name="how-application-manifest-for-trust-works-at-run-time"></a>Güven için uygulama bildirimi çalışma zamanında nasıl çalışır?
 Çalışma zamanında güven için uygulama bildiriminin nasıl çalıştığını daha iyi anlamak için aşağıdaki örneği göz önünde bulundurabilirsiniz. Microsoft ClickOnce 3.5'i .NET Framework bir uygulama oluşturulur. Uygulama bildirimi öğesini kullanır `<useManifestForTrust>` ve Microsoft tarafından imzalanmıştır. Adventure Works, otomatik olarak imzalanan bir sertifika kullanarak dağıtım bildirimini imzalar. Adventure Works istemcileri, Microsoft tarafından imzalanmış herhangi bir uygulamaya güvenerek yapılandırılır.

 Bir kullanıcı dağıtım bildiriminin bağlantısına tıkladığında ClickOnce kullanıcının bilgisayarına uygulama yüklenir. Sertifika ve dağıtım bilgileri, uygulamayı istemci bilgisayarda ClickOnce benzersiz olarak belirtir. Kullanıcı aynı uygulamayı farklı bir konumdan yeniden yüklemeye çalışırsa ClickOnce uygulamanın istemcide zaten var olduğunu belirlemek için bu kimliği kullanabilir.

 Ardından ClickOnce, uygulama bildirimini imzalamak için kullanılan Authenticode sertifikasını inceler ve bu sertifikanın ClickOnce belirler. Adventure Works istemcilerini Microsoft tarafından imzalanmış herhangi bir uygulamaya güvenerek yapılandırmış olduğu için bu ClickOnce tam güvene sahip olur. Daha fazla bilgi için bkz. [Güvenilen uygulama dağıtımına genel bakış.](../deployment/trusted-application-deployment-overview.md)

## <a name="create-customer-deployments-for-earlier-versions"></a>Önceki sürümler için müşteri dağıtımları oluşturma
 Bir geliştirici, ClickOnce eski sürümlerini kullanan müşterilere uygulama dağıtıyorsa .NET Framework? Aşağıdaki bölümlerde, önerilen çeşitli çözümler ve bunların avantajları ve dezavantajları özetlenmiştir.

### <a name="sign-deployments-on-behalf-of-customer"></a>Dağıtımları müşteri adına imzalama
 Olası dağıtım stratejilerinden biri, geliştiricinin, müşterinin kendi özel anahtarını kullanarak dağıtımları müşterileri adına imzalamak için bir mekanizma oluşturmasıdır. Bu, geliştiricinin özel anahtarları veya birden çok dağıtım paketlerini yönetmek zorunda kalmasını önler. Geliştirici her müşteriye aynı dağıtımı sağlar. Müşterinin imzalama hizmetini kullanarak ortamı için özelleştirmesi gerekir.

 Bu yöntemin bir dezavantajı, bunu uygulamak için gereken zaman ve giderdir. Bu tür bir hizmet, .NET Framework SDK'da sağlanan araçlar kullanılarak .NET Framework, ürün yaşam döngüsüne daha fazla geliştirme süresi ekler.

 Bu konu başlığında daha önce belirtildiği gibi, bir diğer dezavantajı da her müşterinin uygulama sürümünün aynı uygulama kimliğine sahip olmasıdır ve bu da çakışmalara neden olabilir. Bu bir sorunsa geliştirici, her uygulamaya benzersiz bir ad vermek için dağıtım bildirimini oluşturma sırasında kullanılan Ad alanını değiştirebilir. Bu, uygulamanın her sürümü için ayrı bir kimlik oluşturma ve olası kimlik çakışmalarını ortadan kaldırma. Bu alan, Mage.exe için bağımsız değişkene ve dosyanın `-Name` **Ad** **sekmesindeki Ad** alanına MageUI.exe.

 Örneğin geliştiricinin Application1 adlı bir uygulama oluşturduğuna göre. Geliştirici, Ad alanı Application1 olarak ayarlanmış tek bir dağıtım oluşturmak yerine application1-CustomerA, Application1-CustomerB gibi bu ad üzerinde müşteriye özgü bir varyasyona sahip birkaç dağıtım oluşturabilir.

### <a name="deploy-using-a-setup-package"></a>Kurulum paketi kullanarak dağıtma
 İkinci olası dağıtım stratejisi, uygulamanın ilk dağıtımını gerçekleştirmek için bir Microsoft Kurulum ClickOnce oluşturmaktır. Bu, birkaç farklı biçimden biri ile sağlanmalıdır: MSI dağıtımı olarak, bir kurulum yürütülebilir dosyası olarak (.EXE) veya bir toplu iş betiğiyle birlikte bir dolap (.cab) dosyası olarak.

 Geliştirici bu tekniği kullanarak müşteriye uygulama dosyalarını, uygulama bildirimini ve şablon olarak görev alan bir dağıtım bildirimini içeren bir dağıtım sağlar. Müşteri kurulum programını çalıştırarak bir dağıtım URL'si (kullanıcıların ClickOnce uygulamasını yükleyecekleri sunucu veya dosya paylaşımı konumu) ve bir dijital sertifika ister. Kurulum uygulaması, güncelleştirme denetimi aralığı gibi ek ClickOnce yapılandırma seçenekleri de istenebilir. Bu bilgiler toplanıp kurulum programı gerçek dağıtım bildirimini üretir, imzalar ve ClickOnce belirtilen sunucu konumunu yayımlar.

 Müşterinin bu durumda dağıtım bildirimini imzalamanın üç yolu vardır:

1. Müşteri, bir sertifika yetkilisi (CA) tarafından verilen geçerli bir sertifika kullanabilir.

2. Bu yaklaşımın bir varyasyonu olarak müşteri dağıtım bildirimini otomatik olarak imzalanan bir sertifikayla imzalamayı seçebilir. Bunun dezavantajı, kullanıcıya yük isteyip yüklemeyip yüklemey olmadığı sorul Publisher uygulamanın "Unknown Publisher" sözcüklerini görüntülemeye neden olmasıdır. Ancak avantajı, küçük müşterilerin sertifika yetkilisi tarafından verilen bir sertifika için gereken zamanı ve paraları harcamasını önlemesidir.

3. Son olarak, geliştirici kurulum paketine kendi otomatik olarak imzalanan sertifikasını içerebilir. Bu, bu konu başlığında daha önce tartışılan uygulama kimliğiyle ilgili olası sorunları ortaya konur.

   Kurulum dağıtım projesi yönteminin dezavantajı, özel bir dağıtım uygulaması oluşturmak için gereken süre ve giderdir.

### <a name="have-customer-generate-deployment-manifest"></a>Müşterinin dağıtım bildirimi oluşturması için
 Üçüncü olası dağıtım stratejisi, yalnızca uygulama dosyalarını ve uygulama bildirimini müşteriye teslim etmektir. Bu senaryoda müşteri, dağıtım bildirimini oluşturmak ve imzalamak .NET Framework SDK'sını kullanmakla sorumludur.

 Bu yöntemin dezavantajı, müşterinin .NET Framework SDK araçlarını yüklemesi ve bunları kullanma becerili bir geliştirici veya sistem yöneticisine sahip olmasıdır. Bazı müşteriler, teknik çalışmaların çok az olduğu veya hiç çalışmamalarının gerekli olduğu bir çözüm talep ediyor olabilir.

## <a name="see-also"></a>Ayrıca bkz.
- [Yeniden ClickOnce test ve üretim sunucuları için uygulama dağıtma](../deployment/deploying-clickonce-applications-for-testing-and-production-without-resigning.md)
- [Adım adım kılavuz: Bir ClickOnce el ile dağıtma](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)
- [Adım adım kılavuz: Yeniden ClickOnce gerektirmeyen ve marka bilgilerini koruyan bir uygulamanın el ile dağıtımı](../deployment/walkthrough-manually-deploying-a-clickonce-app-no-re-signing-required.md)