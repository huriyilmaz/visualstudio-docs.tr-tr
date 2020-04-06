---
title: Proje Tipi Tasarım Kararları | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project types, project file persistence
- project types, commitment mechanics
- project types, items
- project types, design decisions
ms.assetid: f68671fe-fd7a-4e56-a0b5-330b0f1fedb1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5e33ac1c4168593b881f799dfdfb94005fb55fc1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706368"
---
# <a name="project-type-design-decisions"></a>Proje Türü Tasarım Kararları
Yeni bir proje türü oluşturmadan önce, proje türünüzle ilgili birkaç tasarım kararı vermelisiniz. Projelerinizin ne tür öğeler içereceğine, proje dosyalarının nasıl kalıcı olacağına ve hangi bağlılık modelini kullanacağına karar vermeniz gerekir.

## <a name="project-items"></a>Proje Öğeleri
 Projeniz dosyaları veya soyut nesneleri kullanır mı? Dosyaları kullanırsanız, bunlar başvuru tabanlı veya dizin tabanlı dosyalar mı olacak? Dosyalar veya soyut nesneler yerel mi yoksa uzak mı olacak?

 Projedeki öğeler dosya olabilir veya veritabanı deposundaki nesneler veya Internet'teki veri bağlantıları gibi daha soyut nesneler olabilir. Öğeler dosyaysa, proje başvuru tabanlı veya dizin tabanlı bir proje olabilir.

 Başvuru tabanlı projelerde, öğeler birden fazla projede görünebilir. Ancak, bir öğenin temsil ettiği gerçek dosya yalnızca tek bir dizinde bulunur. Dizin tabanlı projelerde, tüm proje öğeleri dizin yapısında bulunur.

 Yerel öğeler, uygulamanın yüklü olduğu aynı bilgisayarda depolanır. Uzak öğeler yerel bir ağda veya Internet'in başka bir yerinde ayrı bir sunucuda depolanabilir.

## <a name="project-file-persistence"></a>Proje Dosyası Kalıcılığı
 Veriler ortak düz dosya sistemlerinde mi yoksa yapılandırılmış depolamada mı depolanacak? Dosyalar standart bir düzenleyici veya projeye özel bir düzenleyici kullanılarak açılacak mı?

 Verilerini kalıcı hale getirmek için, çoğu uygulama verilerini bir dosyaya kaydeder ve kullanıcının bilgileri gözden geçirmesi veya değiştirmesi gerektiğinde yeniden okur.

 Bileşik dosyalar olarak da adlandırılan yapılandırılmış depolama, genellikle birkaç Bileşen Nesne Modeli (COM) nesnelerinin kalıcı verilerini tek bir dosyada depolaması gerektiğinde kullanılır. Yapılandırılmış depolama ile, birkaç farklı yazılım bileşenleri tek bir disk dosyası paylaşabilirsiniz.

 Projenizdeki öğelerin kalıcılığıyla ilgili olarak göz önünde bulundurmanız gereken birkaç seçeneğiniz vardır. Aşağıdaki seçeneklerden herhangi birini gerçekleştirebilirsiniz:

- Değiştirildiğinde her dosyayı ayrı ayrı kaydedin.

- Tek bir **Kaydet** işleminde birçok işlemi yakalayın.

- Dosyaları yerel olarak kaydedin ve ardından bir sunucuda yayımlayın veya öğe uzak bir nesneye veri bağlantısını temsil ettiğinde proje öğelerini kaydetmek için başka bir yaklaşım kullanın.

  Kalıcılık hakkında daha fazla bilgi için [Project Kalıcılığı](../../extensibility/internals/project-persistence.md) ve [Proje Öğelerini Açma ve Kaydetme'ye](../../extensibility/internals/opening-and-saving-project-items.md)bakın.

## <a name="project-commitment-model"></a>Proje Taahhüt Modeli
 Kalıcı veri nesneleri doğrudan modda mı açılacak yoksa işlenecek modda mı?

 Veri nesneleri doğrudan modda açıldığında, verilere yapılan değişiklikler hemen veya kullanıcı dosyayı el ile kaydettiğinde dahil edilir.

 İşlenen mod kullanılarak veri nesneleri açıldığında, değişiklikler bellekte geçici bir konuma kaydedilir ve kullanıcı dosyayı el ile kaydetmeyi seçene kadar kaydedilmez. O zaman, tüm değişiklikler birlikte meydana gelmelidir veya hiçbir değişiklik yapılmaz.

## <a name="see-also"></a>Ayrıca bkz.
- [Denetim Listesi: Yeni Proje Türleri Oluşturma](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Proje Öğelerini Açma ve Kaydetme](../../extensibility/internals/opening-and-saving-project-items.md)
- [Proje Kalıcılığı](../../extensibility/internals/project-persistence.md)
- [Proje Modeli Öğeleri](../../extensibility/internals/elements-of-a-project-model.md)
- [Proje Modeli Çekirdek Bileşenleri](../../extensibility/internals/project-model-core-components.md)
- [Proje Türleri Oluşturma](../../extensibility/internals/creating-project-types.md)
