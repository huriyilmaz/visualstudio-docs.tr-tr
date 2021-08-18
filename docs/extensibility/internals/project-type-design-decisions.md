---
title: Project Tür Tasarımı Kararları | Microsoft Docs
description: Yeni bir proje türü oluşturarak uygulamanızı genişletmeden önce, öğe, proje dosyası kalıcılığı ve taahhüt Visual Studio kararlarını öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project types, project file persistence
- project types, commitment mechanics
- project types, items
- project types, design decisions
ms.assetid: f68671fe-fd7a-4e56-a0b5-330b0f1fedb1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: b22ea9e537adaf0c6178b5c9f7aff1702b84bbcd
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122102382"
---
# <a name="project-type-design-decisions"></a>Proje Türü Tasarım Kararları
Yeni bir proje türü oluşturmadan önce proje türünüzle ilgili birkaç tasarım kararı alalız. Projenizin içerecek öğe türlerine, proje dosyalarının nasıl kalıcı olarak kalıcı olduğuna ve hangi taahhüt modelini kullanacağıza karar verebilirsiniz.

## <a name="project-items"></a>Project Bileşen
 Projeniz dosyaları mı yoksa soyut nesneleri mi kullanıyor? Dosyaları kullanırsanız, bunlar başvuru tabanlı mı yoksa dizin tabanlı dosyalar mı olacak? Dosyalar veya soyut nesneler yerel veya uzak olacak mı?

 Bir projedeki öğeler dosya olabilir veya bir veritabanı deposundaki nesneler veya İnternet üzerinden veri bağlantıları gibi daha soyut nesneler olabilir. Öğeler dosya ise, proje başvuru tabanlı veya dizin tabanlı bir proje olabilir.

 Başvuru tabanlı projelerde öğeler birden fazla projede görünebilir. Ancak, bir öğenin temsil ettiği gerçek dosya yalnızca bir dizinde bulunur. Dizin tabanlı projelerde, tüm proje öğeleri dizin yapısında bulunur.

 Yerel öğeler, uygulamanın yüklandığı bilgisayarda depolanır. Uzak öğeler yerel bir ağ veya İnternet'te başka bir yerde ayrı bir sunucuda depolanmış olabilir.

## <a name="project-file-persistence"></a>Project Dosya Kalıcılığı
 Veriler ortak düz dosya sistemlerinde mi yoksa yapılandırılmış depolamada mı depolanıyor? Dosyalar standart bir düzenleyici veya projeye özgü bir düzenleyici kullanılarak mı açılır?

 Çoğu uygulama, verilerini kalıcı olarak kaydetmek için verilerini bir dosyaya kaydeden ve ardından kullanıcının bilgileri gözden geçirmesi veya değiştirmesi gereken verileri geri okur.

 Bileşik dosyalar olarak da adlandırılan yapılandırılmış depolama, genellikle birkaç Bileşen Nesne Modeli (COM) nesnesinin kalıcı verilerini tek bir dosyada depolaması gerekende kullanılır. Yapılandırılmış depolama ile, birkaç farklı yazılım bileşeni tek bir disk dosyasını paylaşabilir.

 Projenizin öğeleri için kalıcılık ile ilgili olarak göz önünde bulundurabilirsiniz. Aşağıdaki seçeneklerden birini gerçekleştirebilirsiniz:

- Değiştiriken her dosyayı ayrı ayrı kaydedin.

- Tek bir Kaydetme işlemi içinde birçok **işlemi** yakalama.

- Dosyaları yerel olarak kaydedin ve ardından bir sunucuda yayımlayın veya öğe uzak bir nesneye veri bağlantısını temsil ettiği zaman proje öğelerini kaydetmek için başka bir yaklaşım kullanın.

  Kalıcılık hakkında daha fazla bilgi için [bkz. Project Kalıcılık](../../extensibility/internals/project-persistence.md) ve Öğeleri [Açma Project Kaydetme.](../../extensibility/internals/opening-and-saving-project-items.md)

## <a name="project-commitment-model"></a>Project Taahhüt Modeli
 Kalıcı veri nesneleri doğrudan modda mı yoksa işlem modunda mı açılacak?

 Veri nesneleri doğrudan modda açıldığında, verilerde yapılan değişiklikler hemen dahil olur veya kullanıcı dosyayı el ile kaydeder.

 Veri nesneleri işlem modu kullanılarak açıldığında, değişiklikler bellekte geçici bir konuma kaydedilir ve kullanıcı dosyayı el ile kaydetmeyi seçene kadar işlanmaz. Bu sırada, tüm değişikliklerin birlikte gerçekleşmesi gerekir, yoksa hiçbir değişiklik olmaz.

## <a name="see-also"></a>Ayrıca bkz.
- [Yapılacaklar listesi: Yeni Proje Türleri Oluşturma](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Proje Öğelerini Açma ve Kaydetme](../../extensibility/internals/opening-and-saving-project-items.md)
- [Proje Kalıcılığı](../../extensibility/internals/project-persistence.md)
- [Proje Modeli Öğeleri](../../extensibility/internals/elements-of-a-project-model.md)
- [Proje Modeli Çekirdek Bileşenleri](../../extensibility/internals/project-model-core-components.md)
- [Proje Türleri Oluşturma](../../extensibility/internals/creating-project-types.md)
