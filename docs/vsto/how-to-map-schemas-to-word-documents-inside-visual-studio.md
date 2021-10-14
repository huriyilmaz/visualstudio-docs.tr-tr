---
title: 'Nasıl yapılır: Visual Studio içindeki Word belgeleriyle şemaları eşleme'
description: belge Visual Studio açıkken bir XML şemasını Microsoft Office Word belgesiyle nasıl eşleyeceğinizi öğrenin.
titleSuffix: ''
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
ms.openlocfilehash: 68cc1c0dde7e4d6b161e0fcca3086eb3f603ebef
ms.sourcegitcommit: 8fae163333e22a673fd119e1d2da8a1ebfe0e51a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/13/2021
ms.locfileid: "129971900"
---
# <a name="how-to-map-schemas-to-word-documents-inside-visual-studio"></a>Nasıl yapılır: Visual Studio içindeki Word belgeleriyle şemaları eşleme
  **Önemli** bu konu başlığı altında Microsoft Word, microsoft 'un belirli bir işlevselliğin bir uygulamasını kaldırmasıyla ilgili olarak, Birleşik Devletler ve bölgeleri dışında bulunan ya da microsoft tarafından lisanslanan ürünler Microsoft Word 2010 ocak 'tan önce lisanslı olan bireyler ve kuruluşların avantajı ve kullanımı için özel olarak sunulmaktadır.  Microsoft Word özel XML ile ilgili. Microsoft Word ile ilgili bu bilgiler, Birleşik Devletler veya şirket içinde çalışan ya da şirket içinde çalışan veya Microsoft tarafından lisanslanan Microsoft Word, 10 ocak 2010 ' den sonra lisanslı ürünleri kullanan bireyler veya kuruluşlar tarafından okunamaz veya kullanılmıyor olabilir. Bu ürünler, bu tarihten önce lisanslanan ürünlerle aynı veya satın alınmadan ve Birleşik Devletler dışında kullanılmak üzere lisanslanmaz.

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
