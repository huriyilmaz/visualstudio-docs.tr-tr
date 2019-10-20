---
title: Windows Forms uygulamalarında arama tabloları oluşturma | Microsoft Docs
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
- lookup tables
- lookup tables, creating
ms.assetid: 0edd5385-c381-4b17-9096-74e2778db9d5
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3979d08757445e9df5fc159fe7642b04bf74b995
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72630929"
---
# <a name="create-lookup-tables-in-windows-forms-applications"></a>Windows Forms uygulamalarında arama tabloları oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Terim *arama tablosu* , iki ilişkili veri tablosuna bağlanan denetimleri açıklar. Bu arama denetimleri, ikinci tabloda seçilen bir değere göre ilk tablodaki verileri görüntüler.

 Üst tablonun ana düğümünü ( [veri kaynakları penceresi](https://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992)), formunuzdaki ilgili alt tablodaki sütuna zaten bağlı olan bir denetime sürükleyerek arama tabloları oluşturabilirsiniz.

 Örneğin, bir satış veritabanındaki `Orders` tablosunu düşünün. @No__t_0 tablodaki her kayıt, siparişi hangi müşterinin yerleştirdiğini belirten bir `CustomerID` içerir. @No__t_0, `Customers` tablosundaki müşteri kaydına işaret eden bir yabancı anahtardır. Bu senaryoda, **veri kaynakları** penceresinde `Orders` tablosunu genişlettikten sonra ana düğümü **Ayrıntılar**olarak ayarlarsınız. Sonra `CustomerID` sütununu bir <xref:System.Windows.Forms.ComboBox> (veya arama bağlamasını destekleyen başka bir denetim) kullanacak şekilde ayarlayın ve `Orders` düğümünü formunuza sürükleyin. Son olarak, `Customers` düğümünü ilgili sütuna bağlanan denetimin üzerine sürükleyin — bu durumda, <xref:System.Windows.Forms.ComboBox> `CustomerID` sütununa bağlanır.

## <a name="to-databind-a-lookup-control"></a>Arama denetimini bağlamak için

1. **Veri kaynakları** penceresini açın.

    > [!NOTE]
    > Arama tabloları, **veri kaynakları** penceresinde iki ilişkili tablonun veya nesnenin kullanılabilir olmasını gerektirir.

2. Üst tabloyu ve tüm sütunlarını ve ilgili alt tabloyu ve tüm sütunlarını görene kadar **veri kaynakları** penceresindeki düğümleri genişletin.

    > [!NOTE]
    > Alt tablo düğümü, üst tabloda Genişletilebilir alt düğüm olarak görünen düğümdür.

3. Alt tablonun düğümünde denetim listesinden **Ayrıntılar** ' a tıklayarak alt tablonun bırakma türünü **Ayrıntılar** olarak değiştirin. Daha fazla bilgi için bkz. [veri kaynakları penceresinden sürüklerken oluşturulacak denetimi ayarlama](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

4. İki tabloyla ilişkili düğümü bulun (önceki örnekteki `CustomerID` düğümü). Denetim listesinden **ComboBox** ' i seçerek bırakma türünü bir <xref:System.Windows.Forms.ComboBox> değiştirin.

5. Ana alt tablo düğümünü **veri kaynakları** penceresinden formunuzun üzerine sürükleyin.

     Veri sınırlama denetimleri (tanımlayıcı etiketlerle birlikte) ve formda bir araç şeridi (<xref:System.Windows.Forms.BindingNavigator>) görünür. Bir [veri kümesi](../data-tools/dataset-tools-in-visual-studio.md), TableAdapter, <xref:System.Windows.Forms.BindingSource> ve <xref:System.Windows.Forms.BindingNavigator> bileşen tepsisinde görünür.

6. Şimdi ana üst tablo düğümünü **veri kaynakları** penceresinden doğrudan arama denetimine (<xref:System.Windows.Forms.ComboBox>) sürükleyin.

     Arama bağlamaları artık oluşturulmuştur. Denetimde ayarlanan belirli özellikler için aşağıdaki tabloya bakın.

    |Özellik|Ayarın açıklaması|
    |--------------|----------------------------|
    |**DataSource**|Visual Studio bu özelliği denetim üzerine sürüklediğiniz tablo için oluşturulan <xref:System.Windows.Forms.BindingSource> ayarlar (Denetim oluşturulduğunda oluşturulan <xref:System.Windows.Forms.BindingSource> aksine).<br /><br /> Bir ayarlama yapmanız gerekiyorsa bunu, göstermek istediğiniz sütunla tablonun <xref:System.Windows.Forms.BindingSource> ayarlayın.|
    |**Alınan**|Visual Studio bu özelliği, denetimin üzerine sürüklediğiniz tablo için bir dize veri türüne sahip birincil anahtardan sonraki ilk sütuna ayarlar.<br /><br /> Bir ayarlama yapmanız gerekiyorsa bunu, göstermek istediğiniz sütun adı olarak ayarlayın.|
    |**ValueMember**|Visual Studio bu özelliği birincil anahtara katılan ilk sütuna veya anahtar tanımlanmadığında tablodaki ilk sütuna ayarlar.<br /><br /> Bir ayarlama yapmanız gerekiyorsa, bunu tabloda, göstermek istediğiniz sütunu içeren birincil anahtar olarak ayarlayın.|
    |**SelectedValue**|Visual Studio, bu özelliği **veri kaynakları** penceresinden bırakılan özgün sütuna ayarlar.<br /><br /> Bir ayarlama yapmanız gerekiyorsa bunu ilgili tablodaki yabancı anahtar sütununa ayarlayın.|

## <a name="see-also"></a>Ayrıca Bkz.
 [Visual Studio'da verilere Windows Forms denetimleri bağlama](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
