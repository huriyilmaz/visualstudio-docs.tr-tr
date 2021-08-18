---
title: 'Nasıl yapılır: Visual Studio içindeki Word belgeleriyle şemaları eşleme'
description: belge Visual Studio açıkken bir XML şemasını Microsoft Office Word belgesiyle nasıl eşleyeceğinizi öğrenin.
titleSuffix: ''
ms.custom: seodec18, SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XML schemas [Office development in Visual Studio], mapping
- mappings [Office development in Visual Studio], XML schemas to Word documents
- Word [Office development in Visual Studio], mapping XML schemas
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: e14283c61480796e58cd2f5df0b055fb66ce2ac5
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122083446"
---
# <a name="how-to-map-schemas-to-word-documents-inside-visual-studio"></a>Nasıl yapılır: Visual Studio içindeki Word belgeleriyle şemaları eşleme
  **Önemli** bu konu başlığı altında Microsoft Word, microsoft, Microsoft Word 'den özel XML ile ilgili belirli işlevlerin bir uygulamasını kaldırdıkları zaman, Birleşik Devletler ve bölgeleri dışında bulunan Microsoft Word veya 2010 microsoft tarafından lisanslanan ürünlerin ve kuruluşların kullanımı ve kullanımı için özel olarak sunulur. Microsoft Word ile ilgili bu bilgiler, Birleşik Devletler veya şirket içinde çalışan ya da şirket içinde çalışan veya Microsoft tarafından lisanslanan Microsoft Word, 10 ocak 2010 ' den sonra lisanslı ürünleri kullanan bireyler veya kuruluşlar tarafından okunamaz veya kullanılmıyor olabilir. Bu ürünler, bu tarihten önce lisanslanan ürünlerle aynı veya satın alınmadan ve Birleşik Devletler dışında kullanılmak üzere lisanslanmaz.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 Belge Visual Studio açıkken bir XML şemasını belgeyle eşleyebilirsiniz. belge Visual Studio dışında açıldığında kullandığınız Microsoft Office Word araçlarını kullanırsınız. Office projesi, Word çözümünüzü oluşturmadan önce veya sonra şemayı belgeyle eşleştirdiğinizde aynı nesneleri oluşturur.

## <a name="to-map-an-xml-schema-to-a-word-document-in-visual-studio"></a>Bir XML şemasını Visual Studio bir Word belgesiyle eşlemek için

1. Visual Studio içinde Word belgesi veya şablon projesini açın.

2. Odağı tasarımcıya taşımak için belgeye tıklayın.

3. Şeritte **Geliştirici** sekmesine tıklayın.

    > [!NOTE]
    > **Geliştirici** sekmesi görünür değilse, önce onu göstermelisiniz. Daha fazla bilgi için bkz. [nasıl yapılır: Şeritte Geliştirici sekmesini gösterme](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).

4. **XML** grubunda, **şema**' ya tıklayın.

     **Şablonlar ve eklentiler** iletişim kutusu açılır.

5. **XML şeması** sekmesine tıklayın.

6. **Şema ekle**' ye tıklayın.

     **Şema ekle** iletişim kutusu açılır.

7. Şema dosyanıza gidin, dosyayı seçin ve ardından **Aç**' a tıklayın.

     **şema Ayarlar** iletişim kutusu açılır.

8. Bir diğer ad atayın veya şemayı bir diğer ad olmadan eklemek için **Tamam 'a** tıklayın.

9. **Tamam**'a tıklayın.

     **XML yapısı** penceresi açılır.

10. Öğeleri **XML yapısı** penceresinden, belgenizde ilgili denetimlerin oluşturulmasını istediğiniz yerlere sürükleyin.

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: şemaları Visual Studio içindeki çalışma sayfalarına eşleme](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)
- [Belge düzeyi özelleştirmelerde XML şemaları ve verileri](../vsto/xml-schemas-and-data-in-document-level-customizations.md)
