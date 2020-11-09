---
title: Başkalarının dağıtması için ClickOnce uygulamaları oluşturma | Microsoft Docs
description: .NET Framework 3,5 ' de ve önceki .NET Framework sürümlerinde geliştirilen, müşteri tarafından barındırılan ClickOnce uygulamaları hakkında bilgi edinin.
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7379038d1c2bf203f7787e69408ddd9b2e30f372
ms.sourcegitcommit: 0893244403aae9187c9375ecf0e5c221c32c225b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/09/2020
ms.locfileid: "94383007"
---
# <a name="create-clickonce-applications-for-others-to-deploy"></a>Başkalarının dağıtması için ClickOnce uygulamaları oluşturma
ClickOnce dağıtımları oluşturan tüm geliştiriciler uygulamaları kendileri dağıtmayı planlıyor. Bunların birçoğu ClickOnce kullanarak kendi uygulamasını paketleyebilir ve ardından dosyaları büyük bir kuruluş gibi bir müşteriye kapatır. Müşteri, uygulamayı ağı üzerinde barındırmaktan sorumlu olur. Bu konuda 3,5 sürümünden önceki .NET Framework sürümlerinde bu tür dağıtımlarda bulunan bazı sorunlar ele alınmaktadır. Daha sonra, .NET Framework 3,5 ' deki yeni "güven için bildirimi kullan" özelliği kullanılarak sağlanmış yeni bir çözüm açıklanmaktadır. Son olarak, .NET Framework eski sürümlerini kullanmaya devam eden müşteriler için ClickOnce dağıtımları oluşturmaya yönelik önerilen stratejileri de sonlanır.

## <a name="issues-involved-in-creating-deployments-for-customers"></a>Müşteriler için dağıtım oluşturmayla ilgili sorunlar
 Bir müşteriye dağıtım sağlamayı planlarken çeşitli sorunlar oluşur. İlk sorun kod imzalaması ile ilgilidir. Bir ağ üzerinden dağıtılabilmesi için bir ClickOnce dağıtımının dağıtım bildirimi ve uygulama bildiriminin her ikisi de bir dijital sertifikayla imzalanmalıdır. Bu, bildirimleri imzalarken geliştiricinin sertifikasını mı yoksa müşterinin sertifikasını mı kullanacağınızı sorudan oluşur.

 ClickOnce uygulamasının kimliği, dağıtım bildiriminin dijital imzasını temel alarak, hangi sertifikanın kullanılacağı sorusuna önem taşır. Geliştirici dağıtım bildirimini imzalarsa, müşteri büyük bir şirketse ve şirketin birden fazla bölümü uygulamanın özelleştirilmiş bir sürümünü dağıttığında, çakışmalar buna neden olabilir.

 Örneğin, Adventure Works 'ün bir finans departmanı ve insan kaynakları departmanı olduğunu varsayalım. Her iki departman de bir SQL veritabanında depolanan verilerden rapor üreten bir Microsoft Corporation ClickOnce uygulamasını lisansluyor. Microsoft, her departmanı, verileri için özelleştirilmiş bir uygulama sürümü sağlar. Uygulamalar aynı Authenticode sertifikasıyla imzalanmışsa, ClickOnce ikinci uygulamayı birinciyle özdeş olacak şekilde kullanacağından, her iki uygulamayı da kullanmaya çalışan bir Kullanıcı hatayla karşılaşır. Bu durumda, müşteri, uygulama tarafından yerel olarak depolanan verilerin kaybını içeren öngörülemeyen ve istenmeyen yan etkilerle karşılaşabilir.

 Kod imzalama ile ilgili ek bir sorun, `deploymentProvider` dağıtım bildirimindeki öğesidir ve bu, ClickOnce 'a uygulama güncelleştirmelerinin nerede bakacağını söyler. Bu öğe imzalamadan önce dağıtım bildirimine eklenmelidir. Bu öğe daha sonra eklenirse, dağıtım bildiriminin yeniden imzalanması gerekir.

### <a name="require-the-customer-to-sign-the-deployment-manifest"></a>Müşterinin dağıtım bildirimini imzalamasını gerektir
 Benzersiz olmayan dağıtımlarda bu soruna yönelik bir çözüm, geliştirici uygulama bildirimini imzalayave müşterinin dağıtım bildirimini imzalayamidir. Bu yaklaşım işe yarar, ancak diğer sorunlar ortaya koymaktadır. Authenticode sertifikası korunan bir varlık olarak kalması gerektiğinden, müşteri, dağıtımı imzalamak için sertifikayı yalnızca geliştiriciye sunamaz. Müşteri, .NET Framework SDK 'Sı ile ücretsiz sunulan araçları kullanarak dağıtım bildirimini imzalayabilirken, bu, müşterinin sunabileceği veya sağlayabilenden daha fazla teknik bilgi gerektirebilir. Bu gibi durumlarda, geliştirici genellikle müşterinin imza için uygulama sürümünü gönderebileceği bir uygulama, Web sitesi veya başka bir mekanizma oluşturur.

### <a name="the-impact-of-customer-signing-on-clickonce-application-security"></a>ClickOnce uygulama güvenliği üzerinde müşteri imzalanmasının etkisi
 Geliştirici ve müşteri, müşterinin uygulama bildirimini imzalayacağını kabul etse bile, bu durum özellikle güvenilen uygulama dağıtımı için geçerli olduğu gibi uygulamanın kimliğini çevreleyen diğer sorunları da yükseltir. (Bu özellik hakkında daha fazla bilgi için bkz. [Güvenilen uygulama dağıtımına genel bakış](../deployment/trusted-application-deployment-overview.md).) Adventure Works 'ün, Microsoft Corporation tarafından sunulan herhangi bir uygulamanın tam güvenle çalışması için istemci bilgisayarlarını yapılandırmak istediğini varsayalım. Adventure Works dağıtım bildirimini imzalarsa, ClickOnce, uygulamanın güven düzeyini belirlemekte Adventure Work 'ün güvenlik imzasını kullanacaktır.

## <a name="create-customer-deployments-by-using-application-manifest-for-trust"></a>Güven için uygulama bildirimini kullanarak müşteri dağıtımları oluşturma
 .NET Framework 3,5 ' de ClickOnce, geliştiricilere ve müşterilere bildirimlerin nasıl imzalanması gerektiğine ilişkin senaryoya yeni bir çözüm veren yeni bir özellik içerir. ClickOnce uygulama bildirimi, `<useManifestForTrust>` bir geliştiricinin uygulama bildiriminin dijital imzasının güven kararları vermek için kullanılması gerekenler olduğunu işaret etmesini sağlayan adlı yeni bir öğeyi destekler. Geliştirici, bu öğeyi uygulama bildirimine dahil etmek için *Mage.exe* , *MageUI.exe* ve Visual Studio gibi ClickOnce paketleme araçları 'Nı kullanır ve hem yayımcı adını hem de bildirimin uygulamanın adını eklemek için.

 Kullanırken `<useManifestForTrust>` , dağıtım bildiriminin, bir sertifika yetkilisi tarafından verilen bir Authenticode sertifikasıyla imzalanması gerekmez. Bunun yerine, otomatik olarak imzalanan sertifika olarak bilinen ile imzalanabilir. Otomatik olarak imzalanan bir sertifika, standart .NET Framework SDK araçları kullanılarak müşteri ya da geliştirici tarafından oluşturulur ve ardından standart ClickOnce dağıtım araçları kullanılarak dağıtım bildirimine uygulanır. Daha fazla bilgi için bkz. [MakeCert](/windows/desktop/SecCrypto/makecert).

 Dağıtım bildirimi için otomatik olarak imzalanan bir sertifika kullanılması çeşitli avantajlar sunar. Müşterinin kendi Authenticode sertifikasını alması veya oluşturması gereksinimini ortadan kaldırarak, `<useManifestForTrust>` müşterinin dağıtımını basitleştirir, bu da geliştiricinin uygulama üzerinde kendi marka kimliğini korumasına olanak tanır. Sonuç, daha güvenli ve benzersiz uygulama kimliklerine sahip olan imzalanmış dağıtımlar kümesidir. Bu, aynı uygulamanın birden fazla müşteriye dağıtılmasından oluşabilen olası çakışmayı ortadan kaldırır.

 Etkin bir ClickOnce dağıtımı oluşturma hakkında adım adım bilgiler için `<useManifestForTrust>` bkz. [izlenecek yol: yeniden imzalama gerektirmeyen ve marka bilgilerini koruyan bir ClickOnce uygulamasını el ile dağıtma](../deployment/walkthrough-manually-deploying-a-clickonce-app-no-re-signing-required.md).

### <a name="how-application-manifest-for-trust-works-at-run-time"></a>Güven için uygulama bildirimi çalışma zamanında nasıl çalışır
 Güven için uygulama bildiriminin çalışma zamanında nasıl çalıştığını daha iyi anlamak için aşağıdaki örneği göz önünde bulundurun. .NET Framework 3,5 ' i hedefleyen bir ClickOnce uygulaması Microsoft tarafından oluşturulur. Uygulama bildirimi `<useManifestForTrust>` öğesini kullanır ve Microsoft tarafından imzalanır. Adventure Works, otomatik olarak imzalanan bir sertifika kullanarak dağıtım bildirimini imzalar. Adventure Works istemcileri, Microsoft tarafından imzalanan herhangi bir uygulamaya güvenmek üzere yapılandırılır.

 Kullanıcı dağıtım bildirimine bir bağlantıya tıkladığında, ClickOnce uygulamayı kullanıcının bilgisayarına yüklenir. Sertifika ve dağıtım bilgileri, uygulamayı istemci bilgisayardaki ClickOnce 'a benzersiz bir şekilde tanımlar. Kullanıcı farklı bir konumdan aynı uygulamayı yeniden yüklemeyi denediğinde, ClickOnce bu kimliği uygulamanın zaten istemcide bulunduğunu tespit etmek için kullanabilir.

 Daha sonra ClickOnce, uygulama bildirimini imzalamak için kullanılan Authenticode sertifikasını inceleyerek ClickOnce 'ın vereceğiniz güven düzeyini belirler. Adventure Works, istemcilerini Microsoft tarafından imzalanan herhangi bir uygulamaya güvenecek şekilde yapılandırdığından, bu ClickOnce uygulamasına tam güven verilir. Daha fazla bilgi için bkz. [Güvenilen uygulama dağıtımına genel bakış](../deployment/trusted-application-deployment-overview.md).

## <a name="create-customer-deployments-for-earlier-versions"></a>Önceki sürümler için müşteri dağıtımları oluşturma
 Geliştirici, .NET Framework eski sürümlerini kullanan müşterilere ClickOnce uygulamaları dağıtıyor mu? Aşağıdaki bölümlerde, her birinin avantajları ve dezavantajları ile birlikte önerilen birkaç çözüm özetlenmektedir.

### <a name="sign-deployments-on-behalf-of-customer"></a>Dağıtımları müşteri adına imzala
 Olası bir dağıtım stratejisi, geliştiricinin müşterinin kendi özel anahtarını kullanarak dağıtımlarını müşterileri adına imzalaması için bir mekanizma oluşturması içindir. Bu, geliştiricinin özel anahtarları veya birden çok dağıtım paketini yönetmesini önler. Geliştirici, her müşteriye aynı dağıtımı sağlar. İmzalama hizmetini kullanarak kendi ortamları için özelleştirmek müşterinin yaptığı bir hizmettir.

 Bu yöntemin bir dezavantajı, bunu uygulamak için gereken zaman ve masrafdır. Bu tür bir hizmet, .NET Framework SDK 'sında sunulan araçlar kullanılarak oluşturulabilir, ancak ürün yaşam döngüsüne daha fazla geliştirme süresi eklenir.

 Bu konuda daha önce belirtildiği gibi, başka bir sakıncası, her bir müşterinin uygulamanın her sürümünün aynı uygulama kimliğine sahip olması ve bu da çakışmalara yol açabilir. Bu sorun varsa, geliştirici her uygulamaya benzersiz bir ad vermek için dağıtım bildirimini oluştururken kullanılan ad alanını değiştirebilir. Bu, uygulamanın her sürümü için ayrı bir kimlik oluşturur ve olası kimlik çakışmalarını ortadan kaldırır. Bu alan `-Name` Mage.exe bağımsız değişkenine ve MageUI.exe **ad** sekmesindeki **ad** alanına karşılık gelir.

 Örneğin, geliştiricinin Application1 adlı bir uygulama oluşturduğunu varsayalım. Geliştirici, ad alanı Application1 olarak ayarlanmış tek bir dağıtım oluşturmak yerine, bu ad üzerinde Application1-CustomerA, Application1-CustomerB vb. gibi, müşteriye özgü bir çeşitlemesi olan birkaç dağıtım oluşturabilir.

### <a name="deploy-using-a-setup-package"></a>Kurulum paketi kullanarak dağıtma
 Olası ikinci bir dağıtım stratejisi, ClickOnce uygulamasının ilk dağıtımını gerçekleştirmek için bir Microsoft kurulum projesi oluşturmadır. Bu, birden çok farklı biçimden birinde bulunabilir: bir kurulum yürütülebilir dosyası olarak (MSI dağıtımı olarak). EXE) veya bir yığın betiği ile birlikte bir dolap (. cab) dosyası olarak.

 Geliştirici, bu tekniği kullanarak müşteriye uygulama dosyalarını, uygulama bildirimini ve şablon görevi gören bir dağıtım bildirimini içeren bir dağıtım sağlar. Müşteri Kurulum programını çalıştırarak, bir dağıtım URL 'SI (kullanıcıların ClickOnce uygulamasını yükleyecek sunucu veya dosya paylaşımının konumu) ve dijital bir sertifika için istemde bulunan kurulum programını çalıştırır. Kurulum uygulaması güncelleştirme denetim aralığı gibi ek ClickOnce yapılandırma seçenekleri için de istemde bulunabilir. Bu bilgiler toplandıktan sonra, Kurulum programı gerçek dağıtım bildirimini oluşturur, imzalayıp, ClickOnce uygulamasını belirlenen sunucu konumuna yayımlar.

 Müşterinin bu durumda dağıtım bildirimini imzalayabilmenin üç yolu vardır:

1. Müşteri, bir sertifika yetkilisi (CA) tarafından verilen geçerli bir sertifika kullanabilir.

2. Bu yaklaşımın bir çeşitlemesi olan müşteri, kendi dağıtım bildirimini kendinden imzalı bir sertifikayla imzalamayı tercih edebilir. Bunun olumsuz yanı, kullanıcının yüklemeyi isteyip istemediğiniz sorulduğunda uygulamanın "Bilinmeyen Yayımcı" sözcüklerini görüntülemesine neden olacaktır. Ancak avantajı, daha küçük müşterilerin bir sertifika yetkilisi tarafından verilen bir sertifika için gereken zaman ve para harcamasını önlediği bir avantajdır.

3. Son olarak, geliştirici kurulum paketine kendi otomatik olarak imzalanan sertifikasını dahil edebilir. Bu, bu konuda daha önce açıklanan uygulama kimliğiyle ilgili olası sorunları tanıtır.

   Kurulum dağıtımı proje yönteminin dezavantajı, özel bir dağıtım uygulaması oluşturmak için gereken zaman ve masrafdır.

### <a name="have-customer-generate-deployment-manifest"></a>Müşterinin dağıtım bildirimini oluşturma
 Üçüncü olası bir dağıtım stratejisi, müşteriye yalnızca uygulama dosyalarını ve uygulama bildirimini kapatmamasıdır. Bu senaryoda, müşteri, dağıtım bildirimini oluşturmak ve imzalamak için .NET Framework SDK 'sını kullanmaktan sorumludur.

 Bu yöntemin dezavantajı, müşterinin .NET Framework SDK araçlarını yüklemesini ve bunları kullanmaya uygun bir geliştirici veya Sistem Yöneticisi olmasını gerektirmesidir. Bazı müşteriler, bölümleri üzerinde çok az teknik çaba gerektiren bir çözümü talep edebilir.

## <a name="see-also"></a>Ayrıca bkz.
- [Sınama ve üretim sunucuları için teslim etmeden ClickOnce uygulamaları dağıtma](../deployment/deploying-clickonce-applications-for-testing-and-production-without-resigning.md)
- [İzlenecek yol: ClickOnce uygulamasını El Ile dağıtma](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)
- [İzlenecek yol: yeniden imzalama gerektirmeyen ve marka bilgilerini koruyan bir ClickOnce uygulamasını El Ile dağıtma](../deployment/walkthrough-manually-deploying-a-clickonce-app-no-re-signing-required.md)