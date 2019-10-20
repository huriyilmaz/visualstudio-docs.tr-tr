---
title: 'Nasıl yapılır: Bir Hizmetteki Verilere Bağlanma'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- data [Visual Studio], connecting to web services
- data sources, creating from web services
- data [Visual Studio], reading from web services
- reading data, from web services
- web services, reading data
- web services, as data sources
- web services, connecting
ms.assetid: a6b54353-05fe-4e5c-8631-90231fc95504
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 75efb8656d54c02f3126493504506c913a7e0f4a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72642030"
---
# <a name="how-to-connect-to-data-in-a-service"></a>Nasıl yapılır: bir hizmette verilere bağlanma

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

6. **Son**'a tıklayın.

     Veri kaynağı **veri kaynakları** penceresine eklenir.

## <a name="next-steps"></a>Sonraki adımlar

Uygulamanıza işlevsellik eklemek için, **veri kaynakları** penceresinde bir öğe seçin ve bağlantılı denetimler oluşturmak için onu bir form üzerine sürükleyin. Daha fazla bilgi için bkz. [Visual Studio 'da denetimleri verilere bağlama](../data-tools/bind-controls-to-data-in-visual-studio.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Bir WCF veri hizmetine WPF denetimleri bağlama](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md)
- [Visual Studio 'da Windows Communication Foundation Hizmetleri ve WCF veri Hizmetleri](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)