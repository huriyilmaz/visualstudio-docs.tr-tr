---
title: 'Nasıl yapılır: XML kod parçacıklarını kullanma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 3a27375b-81cc-48f6-a884-e1cb8c4f78f5
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4998fbc530cf4350f4a64b0fd527e0764eafce27
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656269"
---
# <a name="how-to-use-xml-snippets"></a>Nasıl yapılır: XML kod parçacıklarını kullanma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

XML Düzenleyicisi kısayol menüsünde aşağıdaki iki komutu kullanarak XML kod parçacıklarını çağırabilirsiniz. **Kod parçacığı Ekle** komutu, Imleç konumuna XML kod parçacığını ekler. Komutuyla **çevreleme** , XML kod parçacığını seçili metnin çevresinde sarmalanmış. Her XML kod parçacığında belirlenen kod parçacığı türleri vardır. Kod parçacığı türleri, kod parçacığının **ekleme parçacığı** komutu, komut **ile çevreleme** veya her ikisi için kullanılabilir olup olmadığını belirtir.

 XML kod parçacığı düzenleyiciye eklendikten sonra, kod parçacığındaki düzenlenebilir alanlar sarı renkle vurgulanır ve imleç ilk düzenlenebilir alana konumlandırılır.

## <a name="insert-snippet"></a>Kod parçacığı Ekle
 Aşağıdaki yordamlarda, **kod parçacığı Ekle** komutuna nasıl erişebileceğiniz açıklanır.

> [!NOTE]
> **Kod parçacığı Ekle** komutu, klavye KıSAYOLU (CTRL + K, sonra CTRL + X) aracılığıyla da kullanılabilir.

#### <a name="to-insert-snippets-from-the-shortcut-menu"></a>Kısayol menüsünden kod parçacıkları eklemek için

1. İmleci XML parçacığı eklemek istediğiniz yere konumlandırın.

2. Sağ tıklayın ve **kod parçacığı Ekle**' yi seçin.

     Kullanılabilir XML kod parçacıklarının listesi görüntülenir.

3. Fareyi kullanarak listeden bir kod parçacığı seçin ya da kod parçacığının adını yazarak sekme veya ENTER tuşuna basın.

#### <a name="to-insert-snippets-using-the-intellisense-menu"></a>IntelliSense menüsünü kullanarak kod parçacıkları eklemek için

1. İmleci XML parçacığı eklemek istediğiniz yere konumlandırın.

2. **Düzenle** menüsünde, **IntelliSense**' ın üzerine gelin ve **kod parçacığı Ekle**' yi seçin.

     Kullanılabilir XML kod parçacıklarının listesi görüntülenir.

3. Fareyi kullanarak veya kod parçacığının adını yazıp TAB veya ENTER tuşuna basarak listeden bir kod parçacığı seçin.

#### <a name="to-insert-snippets-through-the-intellisense-complete-word-list"></a>IntelliSense 'in bir bütün kelime listesinden kod eklemek için

1. İmleci XML parçacığı eklemek istediğiniz yere konumlandırın.

2. Dosyanıza eklemek istediğiniz XML kod parçacığını yazmaya başlayın. Otomatik tamamlama açıksa, IntelliSense Tamam sözcük listesi görüntülenir. Görünmezse, etkinleştirmek için CTRL + Ara çubuğu tuşlarına basın.

3. Tüm sözcük listesinden XML kod parçacığını seçin.

4. XML kod parçacığını çağırmak için TAB ve TAB tuşlarına basın.

> [!NOTE]
> XML parçacığı çağrılmayan durumlar olabilir. Örneğin, bir `xs:element` düğümüne bir `xs:complexType` öğesi eklemeye çalışırsanız, düzenleyici bir XML kod parçacığı oluşturmaz. Bir `xs:element` düğümü içinde `xs:complexType` öğesi kullanıldığında, gerekli öznitelik veya alt öğeler yoktur, bu nedenle düzenleyicide eklenecek veri yoktur.

#### <a name="to-insert-snippets-using-the-shortcut-name"></a>Kısayol adını kullanarak kod parçacıkları eklemek için

1. İmleci XML parçacığı eklemek istediğiniz yere konumlandırın.

2. Düzenleyici bölmesine `<` yazın.

3. IntelliSense Tamam sözcük listesini kapatmak için ESC tuşuna basın.

4. Kod parçacığının kısayol adını yazın ve XML kod parçacığını çağırmak için TAB tuşuna basın.

## <a name="surround-with"></a>Şununla Çevrele
 Aşağıdaki yordamlarda, komutla **birlikte** nasıl erişebileceğiniz açıklanır.

> [!NOTE]
> Komut **Ile çevreleme** , klavye KıSAYOLU (CTRL + K, sonra CTRL + S) aracılığıyla da kullanılabilir.

#### <a name="to-use-surround-with-from-the-context-menu"></a>Bağlam menüsünden ile çevrelemeyi kullanmak için

1. XML düzenleyicisinde çevreleyecek metni seçin.

2. Sağ tıklayıp **birlikte Çevrele**' yi seçin.

     XML parçacıkları ile kullanılabilir çevreler listesi görüntülenir.

3. Fareyi kullanarak listeden bir kod parçacığı seçin ya da kod parçacığının adını yazarak sekme veya ENTER tuşuna basın.

#### <a name="to-use-surround-with-from-the-intellisense-menu"></a>IntelliSense menüsünden ile çevrelemeyi kullanmak için

1. XML düzenleyicisinde çevreleyecek metni seçin.

2. **Düzenle** menüsünde, **IntelliSense**' ın üzerine gelin ve **birlikte Çevrele**' yi seçin.

     XML parçacıkları ile kullanılabilir çevreler listesi görüntülenir.

3. Fareyi kullanarak listeden bir kod parçacığı seçin ya da kod parçacığının adını yazarak sekme veya ENTER tuşuna basın.

## <a name="using-xml-snippets"></a>XML kod parçacıklarını kullanma
 Bir XML parçacığı seçtikten sonra, kod parçacığının metni imleç konumuna otomatik olarak eklenir. Kod parçacığındaki düzenlenebilir alanlar vurgulanır ve ilk düzenlenebilir alan otomatik olarak seçilir. Şu anda seçili olan alan kutulanır.

 Bir alan seçildiğinde, alan için yeni bir değer yazabilirsiniz. Kod parçacığının düzenlenebilir alanları aracılığıyla sekme döngülerine basma SHIFT + TAB tuşlarına basıldığında ters sırada geçiş yapın. Bir alana tıklanması imleci alana koyar ve bir alana çift tıklamak onu seçer. Bir alan vurgulandığında, alanın açıklamasını sunan bir araç Ipucu görüntülenebilir.

 Belirli bir alanın yalnızca ilk örneği düzenlenebilir. Bu alan vurgulandığında, bu alanın diğer örnekleri ana hatlarıyla gösterilir. Düzenlenebilir bir alanın değerini değiştirdiğinizde, bu alan kod parçacığında kullanıldığı her yerde değişir.

 ENTER veya ESC tuşlarına basıldığında alan düzenleme iptal edilir ve düzenleyici normal olarak döndürülür.

 Düzenlenebilir kod parçacığı alanları için varsayılan renkler, **Seçenekler** Iletişim kutusunun **yazı tipi ve renkler** bölmesindeki kod parçacığı alanı ayarı değiştirilerek değiştirilebilir. Daha fazla bilgi için bkz. [nasıl yapılır: düzenleyicideki yazı tiplerini ve renkleri değiştirme](../ide/reference/how-to-change-fonts-and-colors-in-the-editor.md).

## <a name="see-also"></a>Ayrıca Bkz.
 [XML kod parçacıkları](../xml-tools/xml-snippets.md) [nasıl yapılır: xml şemasından XML kod parçacığı](../xml-tools/how-to-generate-an-xml-snippet-from-an-xml-schema.md) [oluşturma nasıl yapılır: XML parçacıkları oluşturma](../xml-tools/how-to-create-xml-snippets.md)
