---
title: Çoklu giriş işareti düzenleme
description: Mac için Visual Studio'da kod düzenlerken metni birden çok konuma ekleyin.
author: cobey
ms.author: cobey
ms.date: 08/19/2019
ms.openlocfilehash: a21bebda057a772017fa1481e18f9801d1fbcbdf
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "75451449"
---
# <a name="multi-caret-editing"></a>Çoklu giriş işareti düzenleme

Çok noktalı düzenleme, tek seferde _n_ sayısı ekleme noktaları eklemenize olanak tanır. Çok yönlü modda, belgenize fare tıklamaları veya klavye komutları aracılığıyla ek bakımlar ekleyebilirsiniz. Birincil caret kırmızı imleç ile gösterilir, ikincil carets açık mavi renkte mevcut iken. Çok bakımlı bir şekilde yapılan dama modu `ESC` tuşu ile devre dışı edilebilir.

## <a name="enabling-multi-caret-editing"></a>Çok bakımlı düzenlemeyi etkinleştirme

### <a name="keyboard"></a>Klavye

Klavye üzerinden çok yönlü modu çeşitli şekillerde etkinleştirebilirsiniz. Aşağıdaki tablo, çok yönlü düzenlemebelirli modları girmek için kullanılabilir klavye kısayolları sağlar:

| Hotkey  | Eylem                        | 
|---------| ------------------------------|
|  ⌥⇧.   | Sonraki eşleşen caret ekleme    | 
|  ⌥⇧;   | Eşleşen tüm tüm bakımları takın | 
|  ⌥⇧,   | Son bakımı kaldırın             | 
|  ⌥⇧/   | Son bakımı aşağı taşıyın          | 

Bu davranışların her biri, komutu çağırdığınızda caret'in geçerli konumuna sabitlenir. Örneğin, bakıcı "ad" sözcüğünün başındaysa ve "Tüm eşleşen carets insert" (;) geçerli belgenizdeki "ad" sözcüğünün her örneği, sözcüğün başında bir özeneklenecektir. Aynı şekilde, "Sonraki eşleşen özeni ekle" (13.) komutunu çağırırsanız, "ad" sözcüğünün bir sonraki örneğine bir basamak yerleştirilir. Bu komut birden çok kez çağrılabilir.

![çok yönlü klavye](media/multi-caret-keyboard.gif)

## <a name="mousetouchpad"></a>Fare/dokunmatik yüzey

İmlecinizi kullanarak, birden fazla okşadığınız için belirli ekleme noktalarını serbestçe seçebilirsiniz. Klavye kısayolları eşleşen dizeleri bağlı olsa da, imleç ile belgenin herhangi bir yerine el ile bir caret ekleyebilirsiniz. Basamaklar ayarlandıktan sonra, her biri klavyenizde yazdığınız tuş girişlerini yansıtacaktır.

Birden fazla okşamak için fareyi kullanmak için, tuşuna basmanız ve basılı tutmanız ve atanın girilmesi istediğiniz yere tıklamanız gerekir. Anahtarlar tutulduğu sürece ekleme modunda olabilirsiniz. Yanlış bir konuma bir basamak eklerseniz, aynı alanı tekrar tıklatarak tutup tıklatarak caret'i kaldırabilirsiniz. Tüm carets onları istediğiniz yerde bulunan bir kez, tuşlarına basarak durdurmak ve yazmaya başlayın. Aşağıdaki GIF, hem bir ekleme noktası kümesini seçerek hem de hatalı olarak ayarlanmış noktaları kaldırarak gösterir.

![çok bakımlı fare](media/multi-caret-mouse.gif)

## <a name="see-also"></a>Ayrıca bkz.

- [Hızlı Eylemler (Windows'ta Visual Studio)](/visualstudio/ide/quick-actions)
- [Refactor kodu (Windows'ta Visual Studio)](/visualstudio/ide/refactoring-in-visual-studio)
