---
title: Visual Studio abonelik düzeylerini değiştirmenin etkileri | Visual Studio 'Nde
author: evanwindom
ms.author: cabuschl
manager: cabuschl
ms.assetid: bb2fa359-8170-4db0-a0c5-d49fc692b0aa
ms.date: 03/18/2021
ms.topic: conceptual
description: Visual Studio abonelik düzeyinizi yükseltmenin veya indirmeyle ilgili etkileri öğrenin.
ms.openlocfilehash: 9774c4b7d2ad127d606879f1cd40bc88ae3b2c6f
ms.sourcegitcommit: 8e74969ff61b609c89b3139434dff5a742c18ff4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2021
ms.locfileid: "128375687"
---
# <a name="what-happens-when-you-change-visual-studio-subscription-levels"></a>Visual Studio abonelik düzeylerini değiştirdiğinizde ne olur?
Visual Studio abonelikler, yazılım, araçlar, hizmetler ve diğer avantajlar, abonelik düzeyinize göre değişir.  Genellikle abonelik düzeyiniz arttıkça, sağladığı avantajların daha güçlü olması gerekir.  

Tek bir abonelik düzeyiyle başlayan ve başka bir düzeye yükselme (yükseltme) ya da azalmış (düşürme) senaryolar olabilir.  Bu senaryolara örnek olarak şunlar verilebilir:
- Visual Studio ıde 'nin daha kapsamlı bir sürümüne veya daha geniş bir yazılım indirmeleri erişimine ihtiyaç duymaya karar verirsiniz, bu nedenle yükseltmeyi tercih edersiniz. 
- Şirketinizin abonelik Yöneticisi, geçerli rolünüzü veya projenize göre abonelik düzeyinizi değiştirmeyi seçebilir veya şirketinizin satın alma planlarındaki değişikliklere göre değişiklik gösterebilir. Örneğin, şirketiniz maliyet tasarrufu sağlamak için satın aldıkları aboneliklerin karışımını değiştirmeyi tercih edebilir.  

Yükseltmeniz veya indirgemeniz ve sahip olduğunuz abonelik düzeyine bağlı olarak, yeni aboneliğinizdeki avantajlara erişmek için işlem yapmanız gerekebilir.

## <a name="how-do-my-benefits-change"></a>Avantajlarım nasıl değişir?
Belirli bir avantaj için göreceğiniz değişiklikler avantaja göre değişir.  Bazı örneklere göz atacağız ve her biri için yükseltmelerin ve eski sürümünün etkilerini tartışacağız.

### <a name="visual-studio-ide"></a>Visual Studio IDE
abonelikleriniz için hangi Visual Studio sürümünün dahil olduğu hakkında bilgi için, [Visual Studio abonelik avantajları sayfasına](https://visualstudio.microsoft.com/vs/benefits/)göz atın. abonelikleriniz kapsamındaki sürümler arasındaki farklar hakkında bilgi edinmek için [Visual Studio 2019 sürümlerini karşılaştır](https://visualstudio.microsoft.com/vs/compare/) sayfasını ziyaret edin.
 
Yükseltmeler: yeni aboneliğinizde belirtilen IDE düzeyine erişebilirsiniz.  Bunu kullanmak için, daha düşük sürümü kaldırmak ve yeni, daha yüksek sürümü yüklemek isteyeceksiniz.  

ESKI sürüme indirgenme: daha yüksek abonelik düzeyinde sunulan sürüm için hala kalıcı olarak kullanım haklarına sahipsiniz.  IDE 'nin bu sürümüne erişmek için oturum açamazsınız, ancak daha yüksek düzeydeki aboneliğe erişimi kaybetmemek için onu bir **ürün anahtarıyla etkinleştirmeniz** gerekir.  Abone portalındaki [ürün anahtarları sayfasını](https://my.visualstudio.com/productkeys) ziyaret ederek bir ürün anahtarı edinebilirsiniz.  Visual Studio için ürün anahtarlarını zaten istemiş olmanız durumunda, istediğiniz anahtarların listesini de dışa aktarabilirsiniz. [Ürün anahtarlarını bulma ve](find-keys.md)alma hakkında daha fazla bilgi edinin.

### <a name="individual-azure-credits"></a>Bireysel Azure kredileri
Tek tek Azure kredilerinin servis birimi abonelik düzeyine göre değişiklik gösterir.  Abonelik düzeyinize bağlı olarak, aylık kredi olarak $0 ile $150 arasında bir yere karşılaşabilirsiniz.  

Visual Studio aboneliğiniz değişirse karşılaşabileceğiniz üç senaryo vardır.  Olası yükseltmelere veya eski sürüme indirgenmelere ek olarak, şirketinizin abonelik yöneticileri, size, farklı bir abonelik KIMLIĞI ile aynı düzeyde bir abonelik atayabilir.  Bu durumların üçü de, Azure aboneliklerinizdeki etkileri aynı--yalnızca tek kredilerin değişebilir. 

Visual Studio aboneliğinizi değiştirmek, kredileri alan azure aboneliğiniz ile bağlantıyı keser ve yeni aboneliğinizde avantajı etkinleştirdiğinizde yeni bir Azure aboneliği oluşturulacaktır.  Bu durumda, eski Azure aboneliği son devre dışı bırakmaya tabi olacaktır.  Bunu önlemek için, aşağıdaki geçici çözümlerden birini seçin:
- Aboneliği Kullandıkça öde ' ye dönüştürün.  Ayrıntılar için [Azure DevTest Kullandıkça Öde Aboneliklerimizi makalesini](vs-azure-payg.md)ziyaret edin.  Bu aboneliğe kredi kartı gibi bir ödeme aracı eklemeniz gerekir. 
- yeni Visual Studio aboneliğinizdeki avantajı kullanarak yeni bir azure aboneliği oluşturun ve eski azure aboneliğindeki mevcut Azure varlıklarını yeni bir aboneliğe aktarın. 
  > [!IMPORTANT]
  > Mevcut Azure varlıklarınızın kaybını önlemek için Azure varlıklarınızı yeni Azure aboneliğinize taşımanız veya mevcut Azure aboneliğini Kullandıkça Öde olarak değiştirmeniz önemlidir. 
 
### <a name="software-downloads"></a>Yazılım indirmeleri
Size sunulan Yazılım İndirmeleri, abonelik düzeyinize göre değişir.  Ayrıntılar için bkz. [kullanılabilir Yazılım İndirmeleri](software-download-list.md) makalemiz makalesi. 

  > [!TIP] 
  > [İndirmeler sayfasında](https://my.visualstudio.com/downloads) gördüğünüz yazılım başlıklarının listesi, oturum açma e-posta adresinize atadığınız en yüksek abonelik düzeyine bağlıdır.  Sahip olduğunuz **en yüksek** abonelik düzeyinde sunulan tüm başlıkları görürsünüz.  örneğin, bir Visual Studio Enterprise aboneliğiniz ve bir Visual Studio Dev Essentials üyeliğiniz varsa, Dev Essentials üyeliğinizden oturum açmış olsanız bile Enterprise aboneliğinize dahil edilen tüm başlıkları görürsünüz.  

### <a name="other-benefits"></a>Diğer avantajlar 
Diğer avantajlarda abonelik düzeylerinin değiştirilmesinin etkileri farklılık gösterebilir.  

#### <a name="benefits-with-a-fixed-length"></a>Sabit uzunlukta avantajlar
İş ortaklarımız tarafından sunulan avantajların birçoğu, sabit uzunlukta olan tekliflerdir.  Bunları abonelik düzeyinizdeki değişikliklerden önce etkinleştirdiyseniz, bunların çoğu etkilenmez ve normal teriminin sonuna kadar size kullanılabilir olmaya devam eder.  örneğin, bir Enterprise aboneliğinin parçası olarak bir eğitim avantajına altı aylık bir abonelik etkinleştirdiyseniz ve Visual Studio aboneliğiniz Visual Studio Professional 'e indirgenirse, eğitim aboneliğinde hala kalan bir zaman vardır.  

#### <a name="benefits-that-require-authentication"></a>Kimlik doğrulaması gerektiren avantajlar
Visual Studio ' de her oturum açışınızda kimliği doğrulanmış bir avantaj kullanıyorsanız, bu avantajlar abonelik düzeyiniz indirgenirse kullanılabilir olmaz.  

#### <a name="benefits-that-are-not-available-in-lower-subscription-levels"></a>Daha düşük abonelik düzeylerinde kullanılamayan avantajlar
Geçerli aboneliğinizde sunulan avantajları kullanıyorsanız ancak sizinki indirgenme aboneliğinden yararlandıysanız, bu avantajlara erişiminizi kaybedebilirsiniz.  

## <a name="support-resources"></a>Destek kaynakları
- Visual Studio abonelikleriyle ilgili satış, abonelik, hesap ve faturalandırma konusunda yardım için, [Visual Studio abonelik desteğiyle](https://my.visualstudio.com/gethelp)iletişim kurun.
- Visual Studio ıde, Azure DevOps veya diğer Visual Studio ürünleri veya hizmetleri hakkında sorularınız mı var?  [Visual Studio desteği](https://visualstudio.microsoft.com/support/)' ni ziyaret edin.

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio belgeleri](/visualstudio/)
- [Azure DevOps belgeleri](/azure/devops/)
- [Azure belgeleri](/azure/)
- [Microsoft 365 belgeleri](/microsoft-365/)

## <a name="next-steps"></a>Sonraki adımlar
- [Azure DevOps](https://azure.microsoft.com/services/devops/) özellikleri hakkında bilgi edinin
- [sürüme göre Visual Studio ıde özellikleri](https://visualstudio.microsoft.com/vs/compare/) hakkında bilgi edinin