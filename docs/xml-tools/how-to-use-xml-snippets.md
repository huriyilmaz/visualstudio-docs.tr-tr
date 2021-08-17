---
title: XML kod parçacıklarını kullanma
description: XML kod parçacıkları eklemek veya bir XML kod parçacığını seçili metnin etrafına sarmak için XML düzenleyicisinde komutları kullanmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 3a27375b-81cc-48f6-a884-e1cb8c4f78f5
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-xml-tools
ms.workload:
- multiple
ms.openlocfilehash: ba7c2f8d398994f0e840769aeb6dd43118c238a9523eca07bac661037b472ff5
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121423689"
---
# <a name="how-to-use-xml-snippets"></a>Nasıl yapılır: XML kod parçacıklarını kullanma

XML düzenleyicisi kısayol menüsünde aşağıdaki iki komutu kullanarak XML kod parçacıklarını çağırabilirsiniz. Kod **Parçacığı Ekle** komutu XML kod parçacığını imleç konumunda ekler. Surround **With komutu,** XML kod parçacığını seçili metnin çevresini sarmalar. Her XML kod parçacığının belirlenmiş kod parçacığı türleri vardır. Kod parçacığı türleri, kod parçacığının  Kod Parçacığı Ekle komutuyla mı, Surround With komutuyla mı yoksa her **ikisinde de** mi kullanılabilir olduğunu belirler.

XML kod parçacığı düzenleyiciye eklendikten sonra, kod parçacığında düzenlenebilir tüm alanlar sarı renkle vurgulanır ve imleç ilk düzenlenebilir alanda konumlanır.

## <a name="insert-snippet"></a>Kod Parçacığı Ekle

Aşağıdaki yordamlar Kod Parçacığı Ekle komutuna **nasıl erişileni** açıklar.

> [!NOTE]
> Kod **Parçacığı Ekle komutu,** klavye kısayolu aracılığıyla da kullanılabilir (**Ctrl** + **K**, ardından **Ctrl** + **X**).

### <a name="to-insert-snippets-from-the-shortcut-menu"></a>Kısayol menüsünden kod parçacıkları eklemek için

1. İmleci XML kod parçacığını eklemek istediğiniz konuma getirin.

2. Sağ tıklayın ve Kod Parçacığı **Ekle'yi seçin.**

   Kullanılabilir XML kod parçacıklarının listesi görüntülenir.

3. Fareyi kullanarak veya kod parçacığının adını yazarak ve Sekme veya Enter tuşuna basarak listeden bir **kod** parçacığı **seçin.**

### <a name="to-insert-snippets-using-the-intellisense-menu"></a>IntelliSense menüsünü kullanarak kod parçacıkları eklemek için

1. İmleci XML kod parçacığını eklemek istediğiniz konuma getirin.

2. Düzenle menüsünde **IntelliSense'in** üzerine gelin ve Kod Parçacığı **Ekle'yi seçin.** 

   Kullanılabilir XML kod parçacıklarının listesi görüntülenir.

3. Fareyle veya kod parçacığının adını yazarak ve Sekme veya Enter tuşuna basarak listeden bir **kod** parçacığı **seçin.**

### <a name="to-insert-snippets-through-the-intellisense-complete-word-list"></a>IntelliSense tam sözcük listesi aracılığıyla kod parçacıkları eklemek için

1. İmleci XML kod parçacığını eklemek istediğiniz konuma getirin.

2. Dosyanıza eklemek istediğiniz XML parçacığını yazmaya başlayın. Otomatik tamamlama açıksa IntelliSense tam sözcük listesi görüntülenir. Görünmüyorsa, etkinleştirmek için **Ctrl** + **Ara Çubuğuna** basın.

3. Tam sözcük listesinden XML kod parçacığını seçin.

4. XML **kod parçacığını** **çağırmak için** Sekme , Sekme tuşuna basın.

> [!NOTE]
> XML kod parçacığı çağrılmayabilecek durumlar olabilir. Örneğin, bir düğümün içine öğe `xs:complexType` eklemeye `xs:element` çalışmanız, düzenleyici bir XML kod parçacığı oluşturmaz. Bir `xs:complexType` öğe bir düğümün içinde kullanılırsa, gerekli öznitelikler veya alt öğe yoktur, bu nedenle düzenleyicide eklanacak `xs:element` veri yoktur.

### <a name="to-insert-snippets-using-the-shortcut-name"></a>Kısayol adını kullanarak kod parçacıkları eklemek için

1. İmleci XML kod parçacığını eklemek istediğiniz konuma getirin.

2. Düzenleyici `<` bölmesine yazın.

3. IntelliSense tam sözcük listesini kapatmak için **Esc** tuşuna basın.

4. Kod parçacığının kısayol adını yazın ve Sekme **tuşuna basarak** XML kod parçacığını çağırın.

## <a name="surround-with"></a>Çevrele

Aşağıdaki yordamlarda Surround With komutuna **nasıl erişebilirsiniz?**

> [!NOTE]
> Surround **With komutu,** klavye kısayolu aracılığıyla da kullanılabilir (**Ctrl** + **K**, ardından **Ctrl** + **S**).

### <a name="to-use-surround-with-from-the-context-menu"></a>Bağlam menüsünden Surround With kullanmak için

1. XML düzenleyicisinde çevrelen metni seçin.

2. Sağ tıklayın ve Ile **Çevrele'yi seçin.**

   XML kod parçacıklarıyla birlikte kullanılabilir çevrelerin listesi görüntülenir.

3. Fareyi kullanarak veya kod parçacığının adını yazarak ve Sekme veya Enter tuşuna basarak listeden bir **kod** parçacığı **seçin.**

### <a name="to-use-surround-with-from-the-intellisense-menu"></a>IntelliSense menüsünden Surround With kullanmak için

1. XML düzenleyicisinde çevrelen metni seçin.

2. Düzenle menüsünde **IntelliSense'in** üzerine gelin ve ardından Surround **With seçeneğini belirleyin.** 

   XML kod parçacıklarıyla birlikte kullanılabilir çevrelerin listesi görüntülenir.

3. Fareyi kullanarak veya kod parçacığının adını yazarak ve Sekme veya Enter tuşuna basarak listeden bir **kod** parçacığı **seçin.**

## <a name="use-xml-snippets"></a>XML kod parçacıklarını kullanma

Bir XML kod parçacığını seçtikten sonra, kod parçacığının metni otomatik olarak imleç konumunda eklenir. Kod parçacığında düzenlenebilir alanlar vurgulanır ve ilk düzenlenebilir alan otomatik olarak seçilir. Seçili olan alan kutu içindedir.

Bir alan seçildiğinde, alan için yeni bir değer yazebilirsiniz. Sekme **tuşuna** basılarak kod parçacığının düzenlenebilir alanları arasında döngüler olur; Shift **Tab** + **tuşuna** basılarak bu sekmeler ters sırada döngüye gelir. Bir alana tıklarsa imleci alana yer ve alana çift tıklar ve bu alana tıklar. Bir alan vurgulanmışsa, alanın açıklamasını sunan bir ToolTip görüntülenebilir.

Yalnızca verilen bir alanın ilk örneği düzenlenebilir. Bu alan vurgulanmışsa, bu alanın diğer örnekleri ana hatlarıyla vurgulanır. Düzenlenebilir bir alanın değerini değiştirebilirsiniz. Bu alan, kod parçacığında kullanılan her yerde değiştirilir.

**Enter veya** **Esc tuşuna** basılarak alan düzenlemesi iptal edilir ve düzenleyici normale döner.

Düzenlenebilir kod parçacığı alanları için varsayılan renkler, Seçenekler  iletişim kutusunun Yazı Tipleri ve Renkler bölmesindeki Kod Parçacığı **Alanı** ayarı **değiştirerek** değiştirilebilir. Daha fazla bilgi için [bkz. Nasıl kullanılır: Düzenleyicide yazı tiplerini ve renkleri değiştirme.](../ide/reference/how-to-change-fonts-and-colors-in-the-editor.md)

## <a name="see-also"></a>Ayrıca bkz.

- [XML kod parçacıkları](../xml-tools/xml-snippets.md)
- [Nasıl yapılır: XML şemasından XML kod parçacığı oluşturma](../xml-tools/how-to-generate-an-xml-snippet-from-an-xml-schema.md)
- [Nasıl yapılır: XML kod parçacıkları oluşturma](../xml-tools/how-to-create-xml-snippets.md)
