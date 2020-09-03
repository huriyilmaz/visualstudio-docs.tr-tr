---
title: Proje türleri ne zaman oluşturulur | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80703427"
---
# <a name="when-to-create-project-types"></a>Proje Türlerinin Oluşturulacağı Durumlar
Yeni bir proje türü oluşturmak, kullanıcılarınız için özelleştirme için temel sağlar [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Ancak, yeni bir proje türü oluşturmak tüm özelleştirmeler için gerekli değildir [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Aşağıdaki kılavuzlar, senaryonuz için yeni bir proje türünün gerekli olup olmadığını belirlemenize yardımcı olmalıdır.

## <a name="create-a-new-project-type"></a>Yeni bir proje türü oluştur
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Aşağıdaki yollarla bir veya daha fazla işlem yapmak için özelleştirmek istiyorsanız bir proje türü oluşturmanız gerekir:

- Derleme, dağıtım, yapılandırma ve kaynak denetimine katılın.

- Hata ayıklama desteği sunar.

- Proje öğelerini **Çözüm Gezgini**görüntüleyin.

- Proje veya **Yeni proje** **Aç** iletişim kutusunu kullanın.

- Proje iç içe geçme desteği.

## <a name="extend-an-existing-project-type"></a>Varolan bir proje türünü genişletme
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Varolan bir proje türünün davranışını değiştirmek veya genişletmek için aşağıdaki yollarla kullanılabilecek yeni bir proje türü oluşturmak isteyebilirsiniz, örneğin, projeler için derleme işlemini değiştirme [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] :

- Birden çok dosya ile tek bir birim olarak çalışın.

- Alt öğelerin hiyerarşisi olarak tek bir dosya görüntüleyin.

- Düzenleyicilerin etrafında bir komut bağlamı görüntüleyin.

- Düzenleyiciler için bir hizmet bağlamı görüntüleyin.

## <a name="use-an-existing-project-type"></a>Varolan bir proje türünü kullan
 Yeni bir proje oluşturmak bazen gerekli değildir. Aşağıdaki tabloda, için proje türü oluşturmanız gereken görevler gösterilmektedir.

|Görev|Açıklama|
|----------|-----------------|
|Komutları işleme|Herhangi bir VSPackage, komutları işleyebilir.|
|Düzenleyici oluşturma|Özel düzenleyiciler kaydedilebilir. Daha fazla bilgi için bkz. [belge pencereleri ve düzenleyicilerle](https://msdn.microsoft.com/library/603625e1-62b6-413a-bc44-089346e166bc).|
|Sahip olan pencereler|Yeni bir proje türü eklemeden araç ve belge pencerelerini de oluşturabilirsiniz.|
|Özellikler penceresi özellikleri gösterme|Tüm nesneler özellikleri kullanıma sunabilir.|

## <a name="create-a-project-subtype"></a>Proje alt türü oluşturma
 Proje alt türlerini, bir yönetilen proje türünü yeni bir proje türü oluşturmak zorunda kalmadan genişletmek için kullanabilirsiniz. Proje alt türleri, Microsoft veya içinde yazılmış yönetilen projeleri genişletmek için COM toplamayı kullanır [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] . COM toplama sayesinde, yönetilen proje sistemi uygulamasının çoğunu yeniden kullanabilir ve toplama ve destekleyici arabirimlerin kullanımı aracılığıyla belirli bir senaryo için özelleştirme yapabilirsiniz. Proje alt türleri hakkında daha fazla bilgi için bkz. [Proje alt türleri](../../extensibility/internals/project-subtypes.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Belge pencereleri ve düzenleyicilerle](https://msdn.microsoft.com/library/603625e1-62b6-413a-bc44-089346e166bc)
- [Yapılacaklar listesi: Yeni Proje Türleri Oluşturma](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Visual Studio’da Hiyerarşiler](../../extensibility/internals/hierarchies-in-visual-studio.md)
