---
title: Ne Zaman Project Türleri | Microsoft Docs
description: Kullanıcılarınızı özelleştirmek için yeni bir proje türünün gerekli olup olmadığını Visual Studio öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project types, conditions for creating
ms.assetid: 26adc860-ee4a-4f5c-95e1-e41b207dd7e6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: c4974d4838955baecd0d0ebcaddecf13329adc14
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122110325"
---
# <a name="when-to-create-project-types"></a>Proje Türlerinin Oluşturulacağı Durumlar
Yeni bir proje türü oluşturmak, kullanıcılarınız için [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] özelleştirmeye temel sağlar. Ancak, tüm özelleştirmeler için yeni bir proje türü [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] oluşturmak gerekli değildir. Aşağıdaki yönergeler, senaryo için yeni bir proje türünün gerekli olup olmadığını belirlemenize yardımcı olmalıdır.

## <a name="create-a-new-project-type"></a>Yeni Bir Project Türü Oluşturma
 Aşağıdaki yöntemlerden birini veya daha fazlasını gerçekleştiracak [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] şekilde özelleştirmek için bir proje türü oluşturmanız gerekir:

- Derleme, dağıtma, yapılandırmalar ve kaynak denetimine katılma.

- Hata ayıklama desteği sun.

- proje öğelerini **Çözüm Gezgini.**

- Open **Project** veya New **Project** iletişim kutusunu kullanın.

- Projeyi iç içe yerleştirme desteği.

## <a name="extend-an-existing-project-type"></a>Mevcut Bir Project Genişletme
 Mevcut bir proje türünün davranışını değiştirmek veya genişletmek için aşağıdaki yollarla kullanabileceğiniz yeni bir proje türü oluşturmak , örneğin, projeler için derleme [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] işlemini değiştirmek istiyor [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] olabilir:

- Tek bir birim olarak birden çok dosyayla çalışma.

- Alt öğe hiyerarşisi olarak tek bir dosya görüntüler.

- Düzenleyiciler çerçevesinde bir komut bağlamı görüntüleme.

- Düzenleyiciler için bir hizmet bağlamı görüntüleme.

## <a name="use-an-existing-project-type"></a>Mevcut Bir Project Kullanma
 Bazen yeni proje oluşturmak gerekli değildir. Aşağıdaki tabloda, proje türü oluşturmak zorunda olmadığınız görevler yer alır.

|Görev|Açıklama|
|----------|-----------------|
|Komutları işleme|Herhangi bir VSPackage komutları işebilir.|
|Düzenleyiciyi bina|Özel düzenleyiciler kayded olabilir. Daha fazla bilgi için [bkz. Belge Windows ve Düzenleyiciler.](/previous-versions/bb165691(v=vs.100))|
|Sahip olan pencereler|Yeni bir proje türü eklemeden hem araç hem de belge pencereleri oluşturabilirsiniz.|
|Özellikler penceresi'de özellikleri Özellikler penceresi|Tüm nesneler özellikleri açığa çıkarabilirsiniz.|

## <a name="create-a-project-subtype"></a>Project Alt Türü Oluşturma
 Yeni bir proje türü oluşturmak zorunda kalmadan yönetilen bir proje türünü genişletmek için proje alt türleri kullanabilirsiniz. Project türleri, Microsoft veya 'de yazılan yönetilen projeleri genişletmek için COM toplama [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] kullanır. COM toplama ile, yönetilen proje sistemi uygulamasının büyük bir fazlasını yeniden kullanabilir ve yine de toplama ve destekleyen arabirimlerin kullanımı aracılığıyla belirli bir senaryo için özelleştirilebilirsiniz. Proje alt türleri hakkında daha fazla bilgi için [bkz. Project Alt Türleri.](../../extensibility/internals/project-subtypes.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Belge Windows ve Düzenleyiciler](/previous-versions/bb165691(v=vs.100))
- [Yapılacaklar listesi: Yeni Proje Türleri Oluşturma](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Visual Studio’da Hiyerarşiler](../../extensibility/internals/hierarchies-in-visual-studio.md)