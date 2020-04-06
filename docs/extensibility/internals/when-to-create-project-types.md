---
title: Proje Türleri Ne Zaman Oluşturulur | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project types, conditions for creating
ms.assetid: 26adc860-ee4a-4f5c-95e1-e41b207dd7e6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 861250dac25288f353cbd5c57f510bf67dadce70
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703427"
---
# <a name="when-to-create-project-types"></a>Proje Türlerinin Oluşturulacağı Durumlar
Yeni bir proje türü oluşturmak, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] kullanıcılarınız için özelleştirme için bir temel sağlar. Ancak, tüm [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] özelleştirmeler için yeni bir proje türü oluşturma gerekli değildir. Aşağıdaki yönergeler, senaryonuz için yeni bir proje türünün gerekli olup olmadığını belirlemenize yardımcı olur.

## <a name="create-a-new-project-type"></a>Yeni Proje Türü Oluşturma
 Aşağıdaki yollardan birinde veya daha fazlasında hareket [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] etmek üzere özelleştirmek istiyorsanız bir proje türü oluşturmanız gerekir:

- Yapı, dağıtma, yapılandırmalara ve kaynak denetimine katılın.

- Hata ayıklama desteği sunun.

- **Çözüm Gezgini'nde**proje öğelerini görüntüleyin.

- **Projeyi Aç** veya **Yeni Proje** iletişim kutusunu kullanın.

- Proje iç içe geçmeyi destekleyin.

## <a name="extend-an-existing-project-type"></a>Varolan Proje Türünü Genişletme
 Varolan bir proje türünün davranışını [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] değiştirmek veya genişletmek için aşağıdaki yollarla kullanabileceğiniz yeni bir proje türü [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] oluşturmak isteyebilirsiniz, örneğin, projeler için yapı işlemini değiştirmek:

- Tek bir birim olarak birden çok dosyayla çalışın.

- Tek bir dosyayı alt öğelerin hiyerarşisi olarak görüntüleyin.

- Düzenleyicilerin etrafında bir komut bağlamı görüntüleyin.

- Düzenleyiciler için bir hizmet bağlamı görüntüleyin.

## <a name="use-an-existing-project-type"></a>Varolan Proje Türünü Kullanma
 Yeni bir proje oluşturmak bazen gerekli değildir. Aşağıdaki tablo, proje türü oluşturmak zorunda olmadığınız görevleri gösterir.

|Görev|Açıklama|
|----------|-----------------|
|Kullanım komutları|Herhangi bir VSPackage komutları işleyebilir.|
|Editör oluşturma|Özel editörler kaydedilebilir. Daha fazla bilgi için [Bkz. Belge Windows ve Düzenleyiciler.](https://msdn.microsoft.com/library/603625e1-62b6-413a-bc44-089346e166bc)|
|Pencere sahibi olmak|Yeni bir proje türü eklemeden hem araç hem de belge pencereleri oluşturabilirsiniz.|
|Özellikler penceresindeki özellikleri açığa çıkarma|Tüm nesneler özellikleri ortaya çıkarabilir.|

## <a name="create-a-project-subtype"></a>Proje Alt Türü Oluşturma
 Yeni bir proje türü oluşturmak zorunda kalmadan yönetilen proje türünü genişletmek için proje alt türlerini kullanabilirsiniz. Proje alt türleri, Microsoft [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] veya [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]. COM toplama ile, yönetilen proje sistemi uygulamasının çoğunu yeniden kullanabilir ve yine de toplama ve destekleyici arabirimleri kullanarak belirli bir senaryo için özelleştirebilirsiniz. Proje alt türleri hakkında daha fazla bilgi için [Bkz. Proje Alt Türleri.](../../extensibility/internals/project-subtypes.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Belge Windows ve Editörler](https://msdn.microsoft.com/library/603625e1-62b6-413a-bc44-089346e166bc)
- [Denetim Listesi: Yeni Proje Türleri Oluşturma](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Visual Studio’da Hiyerarşiler](../../extensibility/internals/hierarchies-in-visual-studio.md)
