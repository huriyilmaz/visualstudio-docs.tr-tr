---
title: WCF veri hizmeti başvurusu ekleme, güncelleştirme veya kaldırma
description: Windows Communication Foundation (WCF) veri hizmeti başvurusunun nasıl ekleneceğini, güncelleştirilmesini veya kaldırılacağını inceleyin.
ms.date: 11/04/2016
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
ms.openlocfilehash: 46834208ab567ce4071c15a488ed14285328371e
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126631364"
---
# <a name="how-to-add-update-or-remove-a-wcf-data-service-reference"></a>Nasıl yapılır: WCF veri hizmeti başvurusu ekleme, güncelleştirme veya kaldırma

::: moniker range="vs-2017"
Bir *hizmet başvurusu* , projenin bir veya daha fazla erişmesini sağlar [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] . Yerel ağda veya Internet 'te geçerli çözümde arama yapmak için **hizmet başvurusu Ekle** iletişim kutusunu kullanın [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] .
::: moniker-end
::: moniker range=">=vs-2019"
Windows Communication Foundation (WCF) veri hizmeti başvurularını yönetmenizi sağlayan **Microsoft WCF Web Service Reference Provider** erişmek için **Çözüm Gezgini** **bağlı hizmetler** düğümünü kullanabilirsiniz.
::: moniker-end

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="add-a-wcf-service-reference"></a>WCF hizmet başvurusu ekleme

### <a name="to-add-a-reference-to-an-external-service"></a>Bir dış hizmete başvuru eklemek için

::: moniker range="vs-2017"

1. **Çözüm Gezgini**, hizmeti eklemek istediğiniz projenin adına sağ tıklayın ve ardından **hizmet başvurusu Ekle**' e tıklayın.

   **Hizmet başvurusu Ekle** iletişim kutusu görüntülenir.

1. **Adres** kutusuna hizmetin URL 'sini girin ve ardından hizmeti aramak için **Git** ' e tıklayın. Hizmet Kullanıcı adı ve parola güvenliği uygularsa, sizden Kullanıcı adı ve parola istenebilir.

    > [!NOTE]
    > Yalnızca güvenilir bir kaynaktan hizmetlere başvurmanız gerekir. Güvenilmeyen bir kaynaktan başvuruları eklemek güvenliği tehlikeye atabilir.

     Ayrıca, geçerli hizmet meta verilerinin bulunduğu önceki 15 URL 'Leri depolayan **Adres** listesinden URL 'yi seçebilirsiniz.

     Arama gerçekleştirilirken bir ilerleme çubuğu görüntülenir. **Durdur**' a tıklayarak aramayı dilediğiniz zaman durdurabilirsiniz.

1. **Hizmetler** listesinde, kullanmak istediğiniz hizmetin düğümünü genişletin ve bir varlık kümesi seçin.

1. **Ad alanı** kutusunda, başvuru için kullanmak istediğiniz ad alanını girin.

1. Başvuruyu projeye eklemek için **Tamam** ' ı tıklatın.

     Bir hizmet istemcisi (proxy) oluşturulur ve hizmeti tanımlayan meta veriler *app.config* dosyasına eklenir.
::: moniker-end
::: moniker range=">=vs-2019"
1. **Çözüm Gezgini**, **bağlı hizmetler** düğümüne çift tıklayın veya dokunun.

   **Hizmetleri Yapılandır** sekmesi açılır.

1. **Microsoft WCF Web Service Reference Provider** seçin.

   **WCF Web Service Reference yapılandır** iletişim kutusu görüntülenir.

   ![WCF Web hizmeti sağlayıcısı iletişim kutusunun ekran görüntüsü](media/vs-2019/configure-wcf-web-service-reference-dialog.png)


1. **URI** kutusuna hizmetin URL 'sini girin ve ardından hizmeti aramak için **Git** ' e tıklayın. Hizmet Kullanıcı adı ve parola güvenliği uygularsa, sizden Kullanıcı adı ve parola istenebilir.

    > [!NOTE]
    > Yalnızca güvenilir bir kaynaktan hizmetlere başvurmanız gerekir. Güvenilmeyen bir kaynaktan başvuruları eklemek güvenliği tehlikeye atabilir.

     Ayrıca, geçerli hizmet meta verilerinin bulunduğu önceki 15 URL 'Leri depolayan **URI** listesinden URL 'yi seçebilirsiniz.

     Arama gerçekleştirilirken bir ilerleme çubuğu görüntülenir. **Durdur**' a tıklayarak aramayı dilediğiniz zaman durdurabilirsiniz.

1. **Hizmetler** listesinde, kullanmak istediğiniz hizmetin düğümünü genişletin ve bir varlık kümesi seçin.

1. **Ad alanı** kutusunda, başvuru için kullanmak istediğiniz ad alanını girin.

1. Başvuruyu projeye eklemek için **son** ' a tıklayın.

     Bir hizmet istemcisi (proxy) oluşturulur ve hizmeti tanımlayan meta veriler *app.config* dosyasına eklenir.

::: moniker-end

### <a name="to-add-a-reference-to-a-service-in-the-current-solution"></a>Geçerli çözümde bir hizmete başvuru eklemek için

::: moniker range="vs-2017"

1. **Çözüm Gezgini**, hizmeti eklemek istediğiniz projenin adına sağ tıklayın ve ardından **hizmet başvurusu Ekle**' e tıklayın.

    **Hizmet başvurusu Ekle** iletişim kutusu görüntülenir.

1. **Bul**'a tıklayın.

    Geçerli Çözümdeki tüm hizmetler (her ikisi [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] ve WCF Hizmetleri) **Hizmetler** listesine eklenir.

1. **Hizmetler** listesinde, kullanmak istediğiniz hizmetin düğümünü genişletin ve bir varlık kümesi seçin.

1. **Ad alanı** kutusunda, başvuru için kullanmak istediğiniz ad alanını girin.

1. Başvuruyu projeye eklemek için **Tamam** ' ı tıklatın.

    Bir hizmet istemcisi (proxy) oluşturulur ve hizmeti tanımlayan meta veriler *app.config* dosyasına eklenir.
::: moniker-end
::: moniker range=">=vs-2019"
1. **Çözüm Gezgini**, **bağlı hizmetler** düğümüne çift tıklayın veya dokunun. 

   **Hizmetleri Yapılandır** sekmesi açılır.

1. **Microsoft WCF Web Service Reference Provider** seçin.

   **WCF Web Service Reference yapılandır** iletişim kutusu görüntülenir.

1. **Bul**'a tıklayın.

    Geçerli Çözümdeki tüm hizmetler (her ikisi [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] ve WCF Hizmetleri) **Hizmetler** listesine eklenir.

1. **Hizmetler** listesinde, kullanmak istediğiniz hizmetin düğümünü genişletin ve bir varlık kümesi seçin.

1. **Ad alanı** kutusunda, başvuru için kullanmak istediğiniz ad alanını girin.

1. Başvuruyu projeye eklemek için **son** ' a tıklayın.

    Bir hizmet istemcisi (proxy) oluşturulur ve hizmeti tanımlayan meta veriler *app.config* dosyasına eklenir.

::: moniker-end

## <a name="update-a-service-reference"></a>Hizmet başvurusunu güncelleştirme

[!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)]Bazen varlık veri modeli değişir. Bu durumda, hizmet başvurusunu güncelleştirmeniz gerekir.

### <a name="to-update-a-service-reference"></a>Bir hizmet başvurusunu güncelleştirmek için

- **Çözüm Gezgini**' de, hizmet başvurusunu sağ tıklatın ve ardından **hizmet başvurusunu Güncelleştir**' e tıklayın.

     Bir ilerleme iletişim kutusu, başvurunun özgün konumundan güncelleştirildiği sırada görüntülenir ve hizmet istemcisi meta verilerde yapılan değişiklikleri yansıtacak şekilde yeniden oluşturulur.

## <a name="remove-a-service-reference"></a>Hizmet başvurusunu kaldır

Bir hizmet başvurusu artık kullanılmıyorsa, çözümünüzü çözümden kaldırabilirsiniz.

### <a name="to-remove-a-service-reference"></a>Bir hizmet başvurusunu kaldırmak için

- **Çözüm Gezgini**, hizmet başvurusunu sağ tıklatın ve ardından **Sil**' e tıklayın.

     Hizmet istemcisi çözümden kaldırılacak ve hizmeti tanımlayan meta veriler *app.config* dosyasından kaldırılacak.

    > [!NOTE]
    > Hizmet başvurusuna başvuruda bulunan kodların el ile kaldırılması gerekir.

## <a name="see-also"></a>Ayrıca bkz.

- [Windows Visual Studio 'de Communication Foundation Hizmetleri ve WCF veri Hizmetleri](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)
