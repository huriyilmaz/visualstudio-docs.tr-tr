---
title: Metni bulma ve değiştirme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.find
- vs.findreplacecontrol
- vs.findreplace.findsymbol
- vs.findreplace.symbol
- findresultswindow
- vs.findreplace.quickreplace
- vs.findsymbol
- vs.findinfiles
- vs.findresults1
- vs,findsymbolwindow
- vs.findreplace.quickfind
- vs.lookin
- vs.replace
helpviewer_keywords:
- text searches
- Replace in Files dialog box
- find, text
- Find in Files dialog box
- find
- text searches, finding and replacing text
- Replace dialog box
- text, finding and replacing
- find, symbol
- find and replace
- replace
- find text
- replacing text
ms.assetid: a62545c3-1570-4d12-99fb-a82607eb35a1
caps.latest.revision: 35
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 025ba2eb95514efc740d1f8f7b3bf674d6bf237a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72645645"
---
# <a name="finding-and-replacing-text"></a>Metin Bulma ve Değiştirme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio Code Editor içindeki metni ve bulma **ve değiştirme** veya **dosyalarda Bul/Değiştir**' i kullanarak **sonuçları bul** penceresi gibi belirli metin tabanlı çıkış pencerelerini bulabilir ve değiştirebilirsiniz. Ayrıca, XAML Tasarımcısı ve Windows Forms Tasarımcısı ve araç pencereleri gibi bazı tasarımcı pencereleri üzerinde arama ve değiştirme de yapabilirsiniz.

 Aramaları geçerli belge, geçerli çözüm veya özel bir klasör kümesiyle kapsamını belirleyebilirsiniz. Ayrıca, çok dosya aramaları için bir dosya adı uzantıları kümesi de belirtebilirsiniz. .NET normal ifadelerini kullanarak arama sözdizimini özelleştirebilirsiniz.

 Normal ifadeleri bulmak ve değiştirmek için bkz. [Visual Studio 'Da normal Ifadeler kullanma](../ide/using-regular-expressions-in-visual-studio.md).

> [!TIP]
> **Bul/komut** kutusu hala bir araç çubuğu denetimi olarak kullanılabilir, ancak artık varsayılan olarak görünmez. **Standart** araç çubuğunda **Düğme Ekle veya Kaldır** ' ı ve ardından **bul**' u seçerek **Bul/komut** kutusunu görüntüleyebilirsiniz. Daha fazla bilgi için bkz. [Bul/komut kutusu](../ide/find-command-box.md).

## <a name="find-and-replace-control"></a>Bul ve Değiştir denetimi
 **Bul ve Değiştir** denetimi, kod Düzenleyicisi penceresinin sağ üst köşesinde görüntülenir. **Bul ve Değiştir** denetimi, geçerli belgede verilen arama dizesinin her oluşumunu hemen vurgular. Arama denetimindeki **Sonrakini Bul** düğmesini veya **Öncekini Bul** düğmesini seçerek bir örnekten diğerine gidebilirsiniz.

 **Bul** metin kutusunun yanındaki düğmeyi seçerek değiştirme seçeneklerine erişebilirsiniz. Tek seferde bir değiştirme yapmak için, **Değiştir** metin kutusunun yanındaki **Sonrakini Değiştir** düğmesini seçin. Tüm eşleşmeleri değiştirmek için **Tümünü Değiştir** düğmesini seçin.

 Eşleşmelerin vurgu rengini değiştirmek için, **Araçlar** menüsünü seçin, **Seçenekler**' i seçin ve ardından **ortam**' ı seçin ve **yazı tipleri ve renkler**' i seçin. **Ayarları göster** listesinde, **metin düzenleyici**' yi seçin ve ardından **öğeleri görüntüle** listesinde, **vurgu bul (uzantı)** öğesini seçin.

### <a name="searching-tool-windows"></a>Araç pencerelerini arama
 **Düzenle** menüsünde **Bul ve Değiştir** ' i seçerek veya (CTRL + F) **Output** , bir kod veya **Find Results** metin penceresinde **bul** denetimini kullanabilirsiniz.

 Bul denetiminin bir sürümü de bazı araç pencereleri için de kullanılabilir. Örneğin, artık, arama kutusuna metin girerek **araç kutusu** penceresindeki denetim listesini filtreleyebilirsiniz. Artık içeriklerini aramanıza izin veren diğer araç pencereleri **Çözüm Gezgini**, **özellikler** penceresi ve **Takım Gezgini**diğerleri arasında yer alır.

## <a name="findreplace-in-files"></a>Dosyalarda Bul/Değiştir
 **Dosyalarınızda Bul/Değiştir** , **Bul ve Değiştir** denetimi gibi çalışarak, aramanız için bir kapsam tanımlayabilmeniz gerekir. Yalnızca geçerli açık dosyada düzenleyicide arama yapabilirsiniz, ancak tüm açık belgeleri, tüm çözümü, geçerli projeyi ve seçili klasör kümelerini de arayabilirsiniz. Dosya adı uzantısına göre de arama yapabilirsiniz. **Dosyalarda Bul/Değiştir** iletişim kutusuna erişmek Için, **Düzenle** menüsünde **Bul ve Değiştir** ' i seçin (veya CTRL + SHIFT + F).

 **Tümünü Bul**' u seçtiğinizde, bir **sonuçları bul** penceresi açılır ve aramanızın eşleşmeleri listelenir. Listede bir sonuç seçildiğinde ilişkili dosya görüntülenir ve eşleşme vurgulanır. Dosya zaten düzenlenmek üzere açık değilse, sekme alanının sağ tarafındaki bir önizleme sekmesinde açılır. **Bul denetimini,** **sonuçları bul** listesinde aramak için kullanabilirsiniz.

### <a name="creating-custom-search-folder-sets"></a>Özel arama klasörü kümeleri oluşturma
 Arama **yeri** kutusunun yanındaki arama **klasörlerini Seç** düğmesini ( **.**..) seçerek bir arama kapsamı tanımlayabilirsiniz. **Arama klasörlerini Seç** iletişim kutusunda, içinde arama yapılacak bir klasör kümesi belirtebilir ve daha sonra yeniden kullanabilmeniz için belirtimi kaydedebilirsiniz. Uzak bir makinedeki klasörleri, yalnızca sürücüsünü yerel makineye eşleştirdiyseniz belirtebilirsiniz.

### <a name="creating-custom-component-sets"></a>Özel bileşen kümeleri oluşturma
 Arama **yeri** kutusunun yanındaki **özel bileşen kümesini Düzenle** düğmesini seçerek, bileşen kümelerini arama kapsamınız olarak tanımlayabilirsiniz. Yüklü .NET veya COM bileşenlerini, çözümünüze dahil olan Visual Studio projelerini veya herhangi bir derlemeyi ya da tür kitaplığını (. dll,. tlb,. olb,. exe veya. ocx) belirtebilirsiniz. Başvuruları aramak için **başvurularda ara** kutusunu seçin.

## <a name="see-also"></a>Ayrıca Bkz.
 [Visual Studio'da Normal İfadeler Kullanma](../ide/using-regular-expressions-in-visual-studio.md)
