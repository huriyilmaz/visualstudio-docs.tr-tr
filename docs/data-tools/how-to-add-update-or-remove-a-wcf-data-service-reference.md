---
title: WCF veri hizmeti başvurusu ekleme, güncelleştirme veya kaldırma
description: Communication Foundation (WCF) veri hizmeti başvurusu Windows, güncelleştirme veya kaldırmayı gözden geçirme.
ms.date: 11/22/2021
ms.custom: SEO-VS-2020
ms.topic: how-to
helpviewer_keywords:
- service references [Visual Studio]
- WCF Data Service reference
- WCF data service references
- ADO.NET service references
- ADO.NET Data Service reference
ms.assetid: 892ebf37-3af4-472e-8744-92837677d611
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 662e93d7796ac9d611c274ace1f419a4f61e6111
ms.sourcegitcommit: 8671132ee0425b273b060fa35c75657e7ae02583
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2021
ms.locfileid: "132924257"
---
# <a name="how-to-add-update-or-remove-a-wcf-data-service-reference"></a>Nasıl kullanılır: WCF veri hizmeti başvurusu ekleme, güncelleştirme veya kaldırma

Hizmet .NET Framework, *bir projenin bir veya* daha fazla 'a erişmesini [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] sağlar. Geçerli **Hizmet Başvurusu Ekle,** yerel olarak, yerel bir ağ üzerinde veya İnternet'te arama yapmak için Hizmet Başvurusu Ekle iletişim [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] kutusunu kullanın.

:::moniker range=">=vs-2019"
.NET Core projeleri için,  **Çözüm Gezgini'daki** Bağlı Hizmetler düğümünü kullanarak **Microsoft WCF Web Service Reference Provider** Communication Foundation (WCF) veri hizmeti başvurularını yönetmenizi sağlayan Windows'a erişebilirsiniz.
:::moniker-end

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="add-a-wcf-service-reference"></a>WCF hizmeti başvurusu ekleme

### <a name="to-add-a-reference-to-an-external-service-net-framework-projects"></a>Dış hizmete başvuru eklemek için (.NET Framework projeleri)

1. Bu **Çözüm Gezgini** içinde, hizmeti eklemek istediğiniz projenin adına sağ tıklayın ve ardından **Hizmet Başvurusu Ekle.**

   Hizmet Başvurusu Ekle  iletişim kutusu görüntülenir.

1. Adres **kutusuna** hizmetin URL'sini girin ve ardından Hizmeti aramak **için Git'e** tıklayın. Hizmet kullanıcı adı ve parola güvenliği uygulayıyorsa, sizden bir kullanıcı adı ve parola istenebilirsiniz.

    > [!NOTE]
    > Hizmetlere yalnızca güvenilir bir kaynaktan başvurabilirsiniz. Güvenilmeyen bir kaynaktan başvuru eklemek güvenliği tehlikeye atmış olabilir.

     Url'yi geçerli hizmet meta **verisinin** bulunduğu önceki 15 URL'yi depolar Adres listesinden de seçebilirsiniz.

     Arama gerçekleştiriliyorken bir ilerleme çubuğu görüntülenir. Durdur'a tıklayarak aramanızı istediğiniz zaman **durdurabilirsiniz.**

1. Hizmetler **listesinde,** kullanmak istediğiniz hizmetin düğümünü genişletin ve bir varlık kümesi seçin.

1. Ad **Alanı** kutusuna, başvuru için kullanmak istediğiniz ad alanını girin.

1. Projeye **başvuru** eklemek için Tamam'a tıklayın.

     Bir hizmet istemcisi (ara sunucu) oluşturulur ve hizmeti açıklayan meta verilerapp.config *eklenir.*

:::moniker range=">=vs-2019"
### <a name="to-add-a-reference-to-an-external-service-net-core-projects-including-net-5-and-later"></a>Dış hizmete başvuru eklemek için (.NET 5 ve sonrası dahil.NET Core projeleri)

1. Bu **Çözüm Gezgini** Bağlı Hizmetler düğümüne çift **tıklayın veya** dokunun.

   Hizmetleri **Yapılandır** sekmesi açılır.

1. **Microsoft WCF Web Service Reference Provider.**

   Yapılandırma **WCF Web Service Reference** iletişim kutusu görüntülenir.

   ![WCF Web Hizmeti Sağlayıcısı iletişim kutusunun ekran görüntüsü](media/vs-2019/configure-wcf-web-service-reference-dialog.png)

1. **URI kutusuna** hizmetin URL'sini girin ve ardından Hizmeti aramak **için Git'e** tıklayın. Hizmet kullanıcı adı ve parola güvenliği uygulayıyorsa, sizden bir kullanıcı adı ve parola istenebilirsiniz.

    > [!NOTE]
    > Hizmetlere yalnızca güvenilir bir kaynaktan başvurabilirsiniz. Güvenilmeyen bir kaynaktan başvuru eklemek güvenliği tehlikeye atmış olabilir.

     Url'yi geçerli hizmet meta verisinin bulunduğu önceki 15 URL'yi depolar **URI** listesinden de seçebilirsiniz.

     Arama gerçekleştiriliyorken bir ilerleme çubuğu görüntülenir. Durdur'a tıklayarak aramanızı istediğiniz zaman **durdurabilirsiniz.**

1. Hizmetler **listesinde,** kullanmak istediğiniz hizmetin düğümünü genişletin ve bir varlık kümesi seçin.

1. Ad **Alanı** kutusuna, başvuru için kullanmak istediğiniz ad alanını girin.

1. Projeye **başvuru** eklemek için Son'a tıklayın.

     Bir hizmet istemcisi (ara sunucu) oluşturulur ve hizmeti açıklayan meta verilerapp.config *eklenir.*
:::moniker-end

### <a name="to-add-a-reference-to-a-service-in-the-current-solution-net-framework-projects"></a>Geçerli çözümdeki bir hizmete başvuru eklemek için (.NET Framework)

1. Bu **Çözüm Gezgini** içinde, hizmeti eklemek istediğiniz projenin adına sağ tıklayın ve ardından **Hizmet Başvurusu Ekle.**

    Hizmet Başvurusu Ekle  iletişim kutusu görüntülenir.

1. **Bul**'a tıklayın.

    Geçerli çözümde yer alan tüm hizmetler (hem [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] hem de WCF hizmetleri) Hizmetler **listesine** eklenir.

1. Hizmetler **listesinde,** kullanmak istediğiniz hizmetin düğümünü genişletin ve bir varlık kümesi seçin.

1. Ad **Alanı** kutusuna, başvuru için kullanmak istediğiniz ad alanını girin.

1. Projeye **başvuru** eklemek için Tamam'a tıklayın.

    Hizmeti açıklayan bir hizmet istemcisi (ara sunucu) oluşturulur ve bu dosyayaapp.config *eklenir.*

:::moniker range=">=vs-2019"

### <a name="to-add-a-reference-to-a-service-in-the-current-solution-net-core-projects"></a>Geçerli çözümdeki bir hizmete başvuru eklemek için (.NET Core projeleri)

1. Bu **Çözüm Gezgini** Bağlı Hizmetler düğümüne çift **tıklayın veya** dokunun. 

   Hizmetleri **Yapılandır** sekmesi açılır.

1. **Microsoft WCF Web Service Reference Provider.**

   Yapılandırma **WCF Web Service Reference** iletişim kutusu görüntülenir.

1. **Bul**'a tıklayın.

    Geçerli çözümde yer alan tüm hizmetler (hem [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] hem de WCF hizmetleri) Hizmetler **listesine** eklenir.

1. Hizmetler **listesinde,** kullanmak istediğiniz hizmetin düğümünü genişletin ve bir varlık kümesi seçin.

1. Ad **Alanı** kutusuna, başvuru için kullanmak istediğiniz ad alanını girin.

1. Projeye **başvuru** eklemek için Son'a tıklayın.

    Hizmeti açıklayan bir hizmet istemcisi (ara sunucu) oluşturulur ve bu dosyayaapp.config *eklenir.*

:::moniker-end

## <a name="update-a-service-reference"></a>Hizmet başvurularını güncelleştirme

Bazen Varlık Veri Modeli değişikliklerin [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] en önemlileri. Bu durumda, hizmet başvurularını güncelleştirmeniz gerekir.

### <a name="to-update-a-service-reference"></a>Hizmet başvurularını güncelleştirmek için

- Bu **Çözüm Gezgini,** hizmet başvurusuna sağ tıklayın ve ardından Hizmet Başvurularını **Güncelleştir'e tıklayın.**

     Başvuru özgün konumdan güncelleştirilirken ve hizmet istemcisi meta verilerde yapılan değişiklikleri yansıtacak şekilde yeniden oluşturulurken bir ilerleme durumu iletişim kutusu görüntülenir.

## <a name="remove-a-service-reference"></a>Hizmet başvurularını kaldırma

Bir hizmet başvurusu artık kullanamasa, bunu çözümünüzden kaldırabilirsiniz.

### <a name="to-remove-a-service-reference"></a>Hizmet başvurularını kaldırmak için

- Bu **Çözüm Gezgini,** hizmet başvurusuna sağ tıklayın ve ardından **Sil'e tıklayın.**

     Hizmet istemcisi çözümden kaldırılır ve hizmeti açıklayan meta verilerapp.config *kaldırılır.*

    > [!NOTE]
    > Hizmet başvurusuna başvurulan tüm kodlar el ile kaldırılmalıdır.

## <a name="see-also"></a>Ayrıca bkz.

- [Windows Communication Foundation Services ve WCF veri Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)
