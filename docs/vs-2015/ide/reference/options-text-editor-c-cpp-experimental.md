---
title: Seçenekler, metin düzenleyici, C-C++, deneysel | Microsoft Docs
ms.date: 11/15/2016
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.C/C++.Experimental
- VS.ToolsOptionsPages.Text_Editor.C%2FC%2B%2B.Experimental
- VS.ToolsOptionsPages.Text_Editor.C\C++.Experimental
ms.assetid: b9e9dda2-350c-460d-b368-37d6c5342eee
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5979363f16f2e9d78a2f50ffbb6511d03146caaa
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74297855"
---
# <a name="options-text-editor-cc-experimental"></a>Seçenekler, Metin Düzenleyici, C/C++, Deneysel
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Bu seçenekleri değiştirerek, C veya C++' de programlarken IntelliSense ve gözatma veritabanı ile ilgili davranışı değiştirebilirsiniz.

 Bu sayfaya erişmek için, **Seçenekler** iletişim kutusunda, sol bölmede, **metin düzenleyici**' yi genişletin, **C++C/** öğesini genişletin ve ardından **deneysel**' ı seçin.

 Bu özellikler, Visual Studio 2015 güncelleştirme 1 RC yüklemesinde bulunabilir.

> [!NOTE]
> Bilgisayarınız, aşağıdaki yönergelerde yer alan Visual Studio kullanıcı arabirimi öğelerinden bazıları için farklı adlar veya konumlar gösterebilir. Sahip olduğunuz Visual Studio sürümü ve kullandığınız ayarlar bu öğeleri belirler. Bkz. [Visual Studio 'Da geliştirme ayarlarını özelleştirme](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="browsingnavigation"></a>Göz atma/gezinme
 **Yeni veritabanı altyapısını etkinleştir** Bu, **Tanıma Git** ve **tüm başvuruları bul**gibi işlemler için veritabanı popülasyonu otomatik olarak hızlandırmalı ve tüm veritabanı işlemlerini daha hızlı (doğrulukta hiçbir kayıp olmadan) hale getirir. (Değişiklikleri uygulamak için çözümünüzü kapatıp yeniden açmanız yeterlidir; Visual Studio 'Yu yeniden başlatmanız gerekmez.)

## <a name="intellisense"></a>IntelliSense
 **Üye listesi nokta-ok** Üye listesi için uygulanabilir olduğunda '. ' yerine '-> ' koyar.

## <a name="refactoring"></a>Yeniden Düzenle
 **Extract Işlevini etkinleştir** Seçili kodu kendi işlevine ayıklayın ve kodu yeni işleve yapılan bir çağrı ile değiştirin. Bu özelliğe erişmek için seçili koda sağ tıklayın ve **hızlı eylemler**' i seçin ya da varsayılan kısayola CTRL + nokta [CTRL +.] tuşlarına basmanız yeterlidir.

 **Imza değiştirmeyi etkinleştir** Bir işlevin parametrelerini ekleyin, yeniden sıralayın ve silin ve değişiklikleri tüm çağrı sitelerine yayın. Bu özelliğe erişmek için, işlevin herhangi bir kullanımına sağ tıklayın ve **hızlı eylemler**' i seçin ya da CTRL + nokta [CTRL +.] varsayılan kısayoluna basın.

## <a name="text-editor"></a>{1&gt;Metin Düzenleyici&lt;1}
 **Kapsamları genişletmeyi etkinleştir** Etkinleştirilirse, metin düzenleyicisine ' {' yazarak seçili metni küme ayraçları ile çevreleyin.

 **Önceliği genişletmeyi etkinleştir** Etkinleştirilirse, metin düzenleyicisine ' (' yazarak seçili metni parantezlerle çevrelemeyi seçebilirsiniz.

 Visual Studio galerisindeki ek metin Düzenleyicisi özellikleri için [buradaki](https://go.microsoft.com/fwlink/?LinkId=692016)listeye bakın. Bir örnek, aşağıdakileri destekleyen [ C++ hızlı düzeltmelerde](https://visualstudiogallery.msdn.microsoft.com/be91feef-8dc3-4f7a-ac9f-f34e7ca5918f)verilmiştir:

- **Eksik #include Ekle** -kodunuzda bilinmeyen semboller için ilgili #include önerilir

- Önceki öğe gibi **ad alanı/tam niteleme simgesini kullanarak ekleme** , ancak ad alanları için

- **Eksik noktalı virgül Ekle**

- **MSDN yardımı** -hata mesajlarınız için MSDN 'yi arayın

  Ampul almak için bir dalgalı çizgi üzerine geldiğinizde ya da varsayılan klavye kısayolunu CTRL + nokta (CTRL +.) kullanabilirsiniz. Klavye kısayolu için, giriş işaretinin belirli bir hata veya belirtece yerleştirilme gereksinimi olmadığına unutmayın; yalnızca bu satırdaki herhangi bir şeyin önerilerini çağırmak için hata ile aynı satırda olabilirsiniz.

## <a name="see-also"></a>Ayrıca Bkz.
 [Dile özgü düzenleyici seçeneklerini ayarlama](../../ide/reference/setting-language-specific-editor-options.md) [içinde C++ yeniden düzenleme (VC blogu)](https://devblogs.microsoft.com/cppblog/all-about-c-refactoring-in-visual-studio-2015-preview/)
