---
title: Project Tasarım kararlarını yazın | Microsoft Docs
description: yeni bir proje türü oluşturarak Visual Studio genişletmenize başlamadan önce, öğe, proje dosyası kalıcılığı ve taahhüt mekanizması tasarım kararları hakkında bilgi edinin.
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
ms.openlocfilehash: 07559518e0873d2392b35594cc5fbff6f7de0c32d1a8810895a8e348da83f4f5
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121401420"
---
# <a name="project-type-design-decisions"></a>Proje Türü Tasarım Kararları
Yeni bir proje türü oluşturmadan önce, proje türü ile ilgili çeşitli tasarım kararları almanız gerekir. Projelerinize hangi öğe türlerinin ekleneceğini, proje dosyalarının nasıl kalıcı olacağını ve hangi taahhüt modelinin kullanılacağını karar vermelisiniz.

## <a name="project-items"></a>Project Öğeler
 Projeniz dosyaları veya soyut nesneleri kullanacak mı? Dosyaları kullanıyorsanız, bunlara başvuru tabanlı veya dizin tabanlı dosyalar olur. Dosyalar veya soyut nesneler yerel veya uzak olacak mı?

 Projedeki öğeler dosyalar olabilir veya bir veritabanı deposundaki nesneler veya Internet üzerindeki veri bağlantıları gibi daha soyut nesneler olabilir. Öğeler dosyalar ise, proje başvuru tabanlı ya da dizin tabanlı bir proje olabilir.

 Başvuru tabanlı projelerde, öğeler birden fazla projede görünebilir. Ancak, bir öğenin temsil ettiği gerçek dosya yalnızca bir dizinde bulunur. Dizin tabanlı projelerde, tüm proje öğeleri dizin yapısında bulunur.

 Yerel öğeler, uygulamanın yüklü olduğu bilgisayarda depolanır. Uzak öğeler, yerel ağdaki ayrı bir sunucuda veya Internet 'te başka bir yerde depolanabilir.

## <a name="project-file-persistence"></a>Project Dosya kalıcılığı
 Veriler ortak düz dosya sistemlerinde mi, yoksa yapılandırılmış depolamada mı depolanacak? Dosyalar standart bir düzenleyici veya projeye özgü bir düzenleyici kullanılarak açılacak mi?

 Verilerini kalıcı hale getirmek için, çoğu uygulama verilerini bir dosyaya kaydeder ve bir kullanıcının bilgileri gözden geçirmesi veya değiştirmesi gerektiğinde onu geri okur.

 Birleşik dosyalar olarak da adlandırılan yapılandırılmış depolama, genellikle birkaç bileşen nesne modeli (COM) nesnesinin kalıcı verilerini tek bir dosyada depolaması gerektiğinde kullanılır. Yapılandırılmış depolama ile, çeşitli farklı yazılım bileşenleri tek bir disk dosyasını paylaşabilir.

 Projenizdeki öğelerin kalıcılığını göz önünde bulundurmanız gereken birkaç seçeneğiniz vardır. Aşağıdaki seçeneklerden herhangi birini yapabilirsiniz:

- Her dosyayı değiştirildiğinde tek tek kaydedin.

- Tek bir **kaydetme** işleminde çok sayıda işlem yakalayın.

- Dosyaları yerel olarak kaydedin ve sonra bir sunucuya yayımlayın veya öğe, uzak bir nesne ile bir veri bağlantısını temsil ettiğinde proje öğelerini kaydetmek için başka bir yaklaşım kullanın.

  kalıcılık hakkında daha fazla bilgi için bkz. [Project kalıcılığı](../../extensibility/internals/project-persistence.md) ve [Project öğeleri açma ve kaydetme](../../extensibility/internals/opening-and-saving-project-items.md).

## <a name="project-commitment-model"></a>Project Taahhüt modeli
 Kalıcı veri nesneleri doğrudan modda veya işlem temelli modda açılacak mı?

 Veri nesneleri doğrudan modda açıldığında, verilerde yapılan değişiklikler anında veya Kullanıcı dosyayı el ile kaydettiğinde eklenir.

 Veri nesneleri işlem temelli mod kullanılarak açıldığında, değişiklikler bellekteki geçici bir konuma kaydedilir ve Kullanıcı el ile dosyayı kaydetmeyi seçinceye kadar kaydedilmez. Bu sırada, tüm değişikliklerin birlikte gerçekleşmesi veya hiçbir değişiklik yapılmayacak olması gerekir.

## <a name="see-also"></a>Ayrıca bkz.
- [Yapılacaklar listesi: Yeni Proje Türleri Oluşturma](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Proje Öğelerini Açma ve Kaydetme](../../extensibility/internals/opening-and-saving-project-items.md)
- [Proje Kalıcılığı](../../extensibility/internals/project-persistence.md)
- [Proje Modeli Öğeleri](../../extensibility/internals/elements-of-a-project-model.md)
- [Proje Modeli Çekirdek Bileşenleri](../../extensibility/internals/project-model-core-components.md)
- [Proje Türleri Oluşturma](../../extensibility/internals/creating-project-types.md)
