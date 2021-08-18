---
title: 'Nasıl yapılır: Bir Hizmetteki Verilere Bağlanma'
description: veri kaynağı yapılandırma sihirbazı 'nı çalıştırarak ve veri kaynağı türü seç sayfasında hizmet ' i seçerek, uygulamanızı bir hizmetten döndürülen verilere Bağlan.
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
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122052752"
---
# <a name="how-to-connect-to-data-in-a-service"></a>nasıl yapılır: bir hizmette verileri Bağlan

Uygulamanızı [veri kaynağı Yapılandırma Sihirbazı](../data-tools/media/data-source-configuration-wizard.png) 'nı çalıştırarak ve **veri kaynağı türü seç** sayfasında **hizmet** ' i seçerek bir hizmetten döndürülen verilere bağlanırsınız.

Sihirbazı tamamladıktan sonra projenize bir hizmet başvurusu eklenir ve [veri kaynakları penceresinde](add-new-data-sources.md#data-sources-window)hemen kullanılabilir.

> [!NOTE]
> **Veri kaynakları** penceresinde görünen öğeler, hizmetin döndürdüğü bilgilere bağımlıdır. Bazı hizmetler, **veri kaynağı Yapılandırma Sihirbazı** için bağlanabilir nesneler oluşturmak için yeterli bilgi sağlamayabilir. Örneğin, hizmet türsüz bir veri kümesi döndürürse, Sihirbaz tamamlandıktan sonra **veri kaynakları** penceresinde hiçbir öğe görünmez. Bunun nedeni, türsüz veri kümelerinin şema sağlamamaları, bu nedenle Sihirbazın veri kaynağını oluşturmak için yeterli bilgiye sahip olmaması.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="to-connect-your-application-to-a-service"></a>Uygulamanızı bir hizmete bağlamak için

1. **Veri** menüsünde **Yeni veri kaynağı Ekle**' ye tıklayın.

2. **Veri kaynağı türü seçin** sayfasında **hizmet** ' i seçin ve ardından **İleri**' ye tıklayın.

3. Kullanmak istediğiniz hizmetin adresini girin veya geçerli çözümde hizmetleri bulmak için **bul** ' a tıklayın ve ardından **Git**' e tıklayın.

4. İsteğe bağlı olarak, varsayılan değer yerine yeni bir **ad alanı** yazabilirsiniz.

    > [!NOTE]
    > **Gelişmiş** ' e tıklayarak [hizmet başvurusunu Yapılandır iletişim kutusunu](../data-tools/configure-service-reference-dialog-box.md)açın.

5. Projenize bir hizmet başvurusu eklemek için **Tamam** ' ı tıklatın.

6. **Finish (Son)** düğmesine tıklayın.

     Veri kaynağı **veri kaynakları** penceresine eklenir.

## <a name="next-steps"></a>Sonraki adımlar

Uygulamanıza işlevsellik eklemek için, **veri kaynakları** penceresinde bir öğe seçin ve bağlantılı denetimler oluşturmak için onu bir form üzerine sürükleyin. Daha fazla bilgi için bkz. [Visual Studio denetimleri verilere bağlama](../data-tools/bind-controls-to-data-in-visual-studio.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Bir WCF veri hizmetine WPF denetimleri bağlama](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md)
- [Windows Visual Studio 'de Communication Foundation Hizmetleri ve WCF veri Hizmetleri](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)
