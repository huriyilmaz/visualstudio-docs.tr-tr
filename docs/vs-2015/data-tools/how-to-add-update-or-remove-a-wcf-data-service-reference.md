---
title: 'Nasıl yapılır: WCF veri hizmeti başvurusu ekleme, güncelleştirme veya kaldırma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
helpviewer_keywords:
- service references [Visual Studio]
- WCF Data Service reference
- WCF data service references
- ADO.NET service references
- ADO.NET Data Service reference
ms.assetid: 892ebf37-3af4-472e-8744-92837677d611
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 89a667e3254be8161d4defb54d524756a5eb02fc
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670015"
---
# <a name="how-to-add-update-or-remove-a-wcf-data-service-reference"></a>Nasıl Yapılır: WCF Veri Hizmeti Başvurusunu Güncelleme veya Kaldırma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir *hizmet başvurusu* , projenin bir veya daha fazla [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)] erişmesini sağlar. Geçerli çözümde, yerel bir ağda veya Internet 'te [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)] aramak için **hizmet başvurusu Ekle** iletişim kutusunu kullanın.

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

## <a name="adding-a-service-reference"></a>Hizmet başvurusu ekleme

#### <a name="to-add-a-reference-to-an-external-service"></a>Bir dış hizmete başvuru eklemek için

1. **Çözüm Gezgini**, hizmeti eklemek istediğiniz projenin adına sağ tıklayın ve ardından **hizmet başvurusu Ekle**' e tıklayın.

     **Hizmet başvurusu Ekle** iletişim kutusu görüntülenir.

2. **Adres** kutusuna hizmetin URL 'sini girin ve ardından hizmeti aramak için **Git** ' e tıklayın. Hizmet Kullanıcı adı ve parola güvenliği uygularsa, sizden Kullanıcı adı ve parola istenebilir.

    > [!NOTE]
    > Yalnızca güvenilir bir kaynaktan hizmetlere başvurmanız gerekir. Güvenilmeyen bir kaynaktan başvuruları eklemek güvenliği tehlikeye atabilir.

     Ayrıca, geçerli hizmet meta verilerinin bulunduğu önceki 15 URL 'Leri depolayan **Adres** listesinden URL 'yi seçebilirsiniz.

     Arama gerçekleştirilirken bir ilerleme çubuğu görüntülenir. **Durdur**' a tıklayarak aramayı dilediğiniz zaman durdurabilirsiniz.

3. **Hizmetler** listesinde, kullanmak istediğiniz hizmetin düğümünü genişletin ve bir varlık kümesi seçin.

4. **Ad alanı** kutusunda, başvuru için kullanmak istediğiniz ad alanını girin.

5. Başvuruyu projeye eklemek için **Tamam** ' ı tıklatın.

     Bir hizmet istemcisi (proxy) oluşturulur ve hizmeti tanımlayan meta veriler App. config dosyasına eklenir.

#### <a name="to-add-a-reference-to-a-service-in-the-current-solution"></a>Geçerli çözümde bir hizmete başvuru eklemek için

1. **Çözüm Gezgini**, hizmeti eklemek istediğiniz projenin adına sağ tıklayın ve ardından **hizmet başvurusu Ekle**' e tıklayın.

     **Hizmet başvurusu Ekle** iletişim kutusu görüntülenir.

2. **Keşfet**' e tıklayın.

     Geçerli Çözümdeki tüm hizmetler (hem [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)] hem de WCF Hizmetleri) **Hizmetler** listesine eklenir.

3. **Hizmetler** listesinde, kullanmak istediğiniz hizmetin düğümünü genişletin ve bir varlık kümesi seçin.

4. **Ad alanı** kutusunda, başvuru için kullanmak istediğiniz ad alanını girin.

5. Başvuruyu projeye eklemek için **Tamam** ' ı tıklatın.

     Bir hizmet istemcisi (proxy) oluşturulur ve hizmeti tanımlayan meta veriler App. config dosyasına eklenir.

## <a name="updating-a-service-reference"></a>Hizmet başvurusunu güncelleştirme
 Bir [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)] Varlık Veri Modeli bazen değişir. Bu durumda, hizmet başvurusunun güncellenmesi gerekir.

#### <a name="to-update-a-service-reference"></a>Bir hizmet başvurusunu güncelleştirmek için

- **Çözüm Gezgini**' de, hizmet başvurusunu sağ tıklatın ve ardından **hizmet başvurusunu Güncelleştir**' e tıklayın.

     Bir ilerleme iletişim kutusu, başvurunun özgün konumundan güncelleştirildiği sırada görüntülenir ve hizmet istemcisi meta verilerde yapılan değişiklikleri yansıtacak şekilde yeniden oluşturulur.

## <a name="removing-a-service-reference"></a>Hizmet başvurusunu kaldırma
 Bir hizmet başvurusu artık kullanılmıyorsa, çözümünüzü çözümden kaldırabilirsiniz.

#### <a name="to-remove-a-service-reference"></a>Bir hizmet başvurusunu kaldırmak için

- **Çözüm Gezgini**, hizmet başvurusunu sağ tıklatın ve ardından **Sil**' e tıklayın.

     Hizmet istemcisi çözümden kaldırılır ve hizmeti tanımlayan meta veriler App. config dosyasından kaldırılır.

    > [!NOTE]
    > Hizmet başvurusuna başvuruda bulunan tüm kodların el ile kaldırılması gerekecektir.

## <a name="see-also"></a>Ayrıca Bkz.
 [Visual Studio'da Windows Communication Foundation Hizmetleri ve WCF Veri Hizmetleri](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)
