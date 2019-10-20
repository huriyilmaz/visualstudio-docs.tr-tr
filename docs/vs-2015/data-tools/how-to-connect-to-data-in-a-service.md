---
title: 'Nasıl yapılır: bir hizmette verilere bağlanma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data [Visual Studio], connecting to Web services
- data sources, creating from Web services
- data [Visual Studio], reading from Web services
- reading data, from Web services
- Web services, reading data
- Web services, as data sources
- Web services, connecting
ms.assetid: a6b54353-05fe-4e5c-8631-90231fc95504
caps.latest.revision: 35
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d9bfa6c776e3a2137f751d4253feb0239811d95a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72654696"
---
# <a name="how-to-connect-to-data-in-a-service"></a>Nasıl yapılır: Bir Hizmetteki Verilere Bağlanma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Uygulamanızı [veri kaynağı Yapılandırma Sihirbazı](https://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f) 'nı çalıştırarak ve **veri kaynağı türü seç** sayfasında **hizmet** ' i seçerek bir hizmetten döndürülen verilere bağlanırsınız.

 Sihirbazı tamamladıktan sonra projenize bir hizmet başvurusu eklenir ve [veri kaynakları penceresinde](https://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992)hemen kullanılabilir.

> [!NOTE]
> **Veri kaynakları** penceresinde görünen öğeler, hizmetin döndürdüğü bilgilere bağımlıdır. Bazı hizmetler, **veri kaynağı Yapılandırma Sihirbazı** için bağlanabilir nesneler oluşturmak için yeterli bilgi sağlamayabilir. Örneğin, hizmet türsüz bir veri kümesi döndürürse, Sihirbaz tamamlandıktan sonra **veri kaynakları penceresinde** hiçbir öğe görünmez. Bunun nedeni, türsüz veri kümelerinin şema sağlamamaları, bu nedenle Sihirbazın veri kaynağını oluşturmak için yeterli bilgiye sahip olmaması.

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

### <a name="to-connect-your-application-to-a-service"></a>Uygulamanızı bir hizmete bağlamak için

1. **Veri** menüsünde **Yeni veri kaynağı Ekle**' ye tıklayın.

2. **Veri kaynağı türü seçin** sayfasında **hizmet** ' i seçin ve ardından **İleri**' ye tıklayın.

3. Kullanmak istediğiniz hizmetin adresini girin veya geçerli çözümde hizmetleri bulmak için **bul** ' a tıklayın ve ardından **Git**' e tıklayın.

4. İsteğe bağlı olarak, varsayılan değerin yerine yeni bir **ad alanı** yazılabilir.

    > [!NOTE]
    > **Gelişmiş** ' e tıklayarak [hizmet başvurusunu Yapılandır iletişim kutusunu](../data-tools/configure-service-reference-dialog-box.md)açın.

5. Projenize bir hizmet başvurusu eklemek için **Tamam** ' ı tıklatın.

6. **Son**'a tıklayın.

     Veri kaynağı **veri kaynakları** penceresine eklenir.

## <a name="next-steps"></a>Sonraki Adımlar

#### <a name="to-add-functionality-to-your-application"></a>Uygulamanıza işlevsellik eklemek için

- **Veri kaynakları** penceresinde bir öğe seçin ve bağlantılı denetimler oluşturmak için bu öğeyi bir form üzerine sürükleyin. Daha fazla bilgi için bkz. [Visual Studio 'da denetimleri verilere bağlama](../data-tools/bind-controls-to-data-in-visual-studio.md).

## <a name="see-also"></a>Ayrıca Bkz.
 [Visual Studio 'da Windows Communication Foundation Hizmetleri ve WCF veri Hizmetleri](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md) [bir WCF veri hizmetine WPF denetimleri bağlama](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md)
