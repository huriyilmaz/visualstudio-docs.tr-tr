---
title: 'Nasıl yapılır: Bir Hizmetteki Verilere Bağlanma'
description: Bağlan Kaynak Yapılandırma Sihirbazı'nı çalıştırarak ve Veri Kaynağı Türü Seçin sayfasında Hizmet'i seçerek, bir hizmetten döndürülen verilere uygulamanıza ekleyin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- data [Visual Studio], connecting to web services
- data sources, creating from web services
- data [Visual Studio], reading from web services
- reading data, from web services
- web services, reading data
- web services, as data sources
- web services, connecting
ms.assetid: a6b54353-05fe-4e5c-8631-90231fc95504
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 6854b1cd7647f6bc4ac7ca92c920f7454b7ab1fe
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126631341"
---
# <a name="how-to-connect-to-data-in-a-service"></a>Nasıl kullanılır: Bağlan verilerine veri toplama

Veri Kaynağı Yapılandırma Sihirbazı'nı çalıştırarak ve [](../data-tools/media/data-source-configuration-wizard.png) Veri Kaynağı Türü  Seçin sayfasında Hizmet'i seçerek, bir hizmetten döndürülen verilere **uygulamanıza bağlanabilirsiniz.**

Sihirbaz tamamlandıktan sonra projenize bir hizmet başvurusu eklenir ve Veri Kaynakları penceresinde [hemen kullanılabilir.](add-new-data-sources.md#data-sources-window)

> [!NOTE]
> Veri Kaynakları penceresinde görünen **öğeler,** hizmetin döndüren bilgilere bağlıdır. Bazı hizmetler, Veri Kaynağı Yapılandırma Sihirbazı'nın **bağlanabilir nesneler oluşturması** için yeterli bilgi sağlamayabilir. Örneğin, hizmet türlanmamış bir veri kümesi döndürürse, sihirbazı  tamamladıktan sonra Veri Kaynakları penceresinde hiçbir öğe görünmez. Bunun nedeni, yazlanmamış veri kümelerini şema sağlamamış olmasıdır, bu nedenle sihirbazda veri kaynağını oluşturmak için yeterli bilgi yok.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="to-connect-your-application-to-a-service"></a>Uygulamalarınızı bir hizmete bağlamak için

1. Veri menüsünde **Yeni** Veri Kaynağı **Ekle'ye tıklayın.**

2. Veri **Kaynağı** Türü **Seçin sayfasında Hizmet'i seçin** ve ardından Sonraki'ye **tıklayın.**

3. Kullanmak istediğiniz hizmetin adresini girin veya geçerli çözümde hizmetleri bulmak için **Bul'a** tıklayın ve ardından Git'e **tıklayın.**

4. İsteğe bağlı olarak, varsayılan **değerin yerine** yeni bir Ad Alanı yazebilirsiniz.

    > [!NOTE]
    > Hizmet **Başvurularını** Yapılandır iletişim [kutusunu açmak için Gelişmiş'e tıklayın.](../data-tools/configure-service-reference-dialog-box.md)

5. **Projenize** hizmet başvurusu eklemek için Tamam'a tıklayın.

6. **Finish (Son)** düğmesine tıklayın.

     Veri kaynağı, Veri Kaynakları **penceresine** eklenir.

## <a name="next-steps"></a>Sonraki adımlar

Uygulamanıza işlevsellik eklemek için Veri Kaynakları penceresinde bir öğe **seçin ve** bir forma sürükleyerek bağlı denetimler oluşturun. Daha fazla bilgi için [bkz. denetimlerini Visual Studio.](../data-tools/bind-controls-to-data-in-visual-studio.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Bir WCF veri hizmetine WPF denetimleri bağlama](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md)
- [Windows Visual Studio'de Communication Foundation Services ve WCF veri Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)
