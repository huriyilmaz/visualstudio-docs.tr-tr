---
title: 'Nasıl yapılır: şemaları Visual Studio içindeki Word belgeleriyle eşleme'
description: Visual Studio 'da belge açıkken bir XML şemasını Microsoft Office Word belgesiyle nasıl eşleyeceğinizi öğrenin.
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 427e2fcb9b881305c160b906262f251d32d70981
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/08/2020
ms.locfileid: "96848228"
---
# <a name="how-to-map-schemas-to-word-documents-inside-visual-studio"></a>Nasıl yapılır: şemaları Visual Studio içindeki Word belgeleriyle eşleme
  **Önemli** Microsoft Word ile ilgili bu konu başlığı altında verilen bilgiler, Microsoft Word 'deki özel XML ile ilgili belirli bir işlevselliğin uygulanmasını kaldırdıkları zaman, Birleşik Devletler ve bölgeleri dışında bulunan veya Microsoft tarafından Microsoft tarafından lisanslanan Microsoft Word ürünleri, Microsoft 'un Microsoft Word ile ilgili belirli işlevlerin bir uygulamasını kaldırdığınızda Microsoft 'un 2010 Ocak 'tan önce lisanslı olduğu kişiler ve kuruluşların avantajı ve kullanımı için özel olarak sunulur. Microsoft Word ile ilgili bu bilgiler, Birleşik Devletler veya şirket içinde çalışan ya da Microsoft tarafından, 10 Ocak 2010 ' den sonra Microsoft tarafından lisanslanan Microsoft Word ürünlerini kullanan bireyler veya kuruluşlar tarafından okunamaz veya kullanılmıyor olabilir. Bu ürünler, bu tarihten önce lisanslanan ürünlerle aynı veya satın alınmadan ve Birleşik Devletler dışında kullanılmak üzere lisanslanmaz.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 Visual Studio 'da belge açıkken bir XML şemasını belgeyle eşleyebilirsiniz. Belge Visual Studio dışında açıldığında kullandığınız Microsoft Office Word araçlarını kullanırsınız. Office projesi, Word çözümünüzü oluşturmadan önce veya sonra şemayı belgeyle eşleştirdiğinizde aynı nesneleri oluşturur.

## <a name="to-map-an-xml-schema-to-a-word-document-in-visual-studio"></a>Visual Studio 'da bir Word belgesi ile bir XML şemasını eşlemek için

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

     **Şema ayarları** iletişim kutusu açılır.

8. Bir diğer ad atayın veya şemayı bir diğer ad olmadan eklemek için **Tamam 'a** tıklayın.

9. **Tamam** düğmesine tıklayın.

     **XML yapısı** penceresi açılır.

10. Öğeleri **XML yapısı** penceresinden, belgenizde ilgili denetimlerin oluşturulmasını istediğiniz yerlere sürükleyin.

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: şemaları Visual Studio içindeki çalışma sayfalarına eşleme](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)
- [Belge düzeyi özelleştirmelerde XML şemaları ve verileri](../vsto/xml-schemas-and-data-in-document-level-customizations.md)
