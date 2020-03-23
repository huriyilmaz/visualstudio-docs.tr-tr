---
title: Dış araçları yönetme
ms.date: 11/20/2017
ms.topic: conceptual
f1_keywords:
- vs.externaltools
helpviewer_keywords:
- external tools [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0f22c687f88c7736d5c088ebc28ff490c4c16b8f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591300"
---
# <a name="manage-external-tools"></a>Dış araçları yönetme

**Araçlar** menüsünü kullanarak Visual Studio'nun içinden harici araçları arayabilirsiniz. **Araçlar** menüsünden birkaç varsayılan araç mevcuttur ve kendi çalıştırılabilir diğer çalıştırılabilir ler ekleyerek menüyü özelleştirebilirsiniz.

## <a name="tools-available-on-the-tools-menu"></a>Araçlar menüsünde bulunan araçlar

**Araçlar** menüsü, aşağıdakiler dahil olmak üzere birkaç yerleşik komut içerir:

::: moniker range="vs-2017"

* [Görsel Stüdyo Uzantılarını Yönetmek](finding-and-using-visual-studio-extensions.md) için **Uzantılar ve Güncellemeler**
* Kod **Parçacıkları Yöneticisi** Kod [Parçacıkları Düzenlemek](code-snippets.md) için
* [Menüleri ve araç çubuklarını özelleştirmek](how-to-customize-menus-and-toolbars-in-visual-studio.md) için **özelleştir**
* Visual [Studio IDE ve diğer araçlar için çeşitli seçenekler ayarlama](reference/options-dialog-box-visual-studio.md) **seçenekleri**

::: moniker-end

::: moniker range=">=vs-2019"

* Kod **Parçacıkları Yöneticisi** Kod [Parçacıkları Düzenlemek](code-snippets.md) için
* [Menüleri ve araç çubuklarını özelleştirmek](how-to-customize-menus-and-toolbars-in-visual-studio.md) için **özelleştir**
* Visual [Studio IDE ve diğer araçlar için çeşitli seçenekler ayarlama](reference/options-dialog-box-visual-studio.md) **seçenekleri**

::: moniker-end

## <a name="add-new-tools-to-the-tools-menu"></a>Araçlar menüsüne yeni araçlar ekleme

**Araçlar** menüsünde görünmesi için harici bir araç ekleyebilirsiniz.

1.  >  **Araçlar** **Dış** **Araçlar**seçerek Dış Araçlar iletişim kutusunu açın.

1. **Ekle'yi**tıklatın ve ardından bilgileri doldurun. Örneğin, aşağıdaki **giriş, Windows Gezgini'nin** Visual Studio'da şu anda açık olan dosyanın dizininde açılmasına neden olur:

   * Başlık:`Open File Location`

   * Komut:`explorer.exe`

   * Bağımsız değişken:`/root, "$(ItemDir)"`

   ![Dış Araçlar iletişim kutusu](media/external-tools-dialog.png)

Harici bir araç tanımlanırken kullanılabilecek bağımsız değişkenlerin tam listesi aşağıda veda edilsin:

|Adı|Bağımsız Değişken|Açıklama|
|----------|--------------|-----------------|
|Öğe Yolu|$(ItemPath)|Geçerli dosyanın tam dosya adı (sürücü + yol + dosya adı).|
|Öğe Dizini|$(ItemDir)|Geçerli dosyanın dizini (sürücü + yol).|
|Madde Dosya Adı|$(ItemFilename)|Geçerli dosyanın dosya adı (dosya adı).|
|Öğe Uzantısı|$(ItemExt)|Geçerli dosyanın dosya adı uzantısı.|
|Geçerli Hat|$(CurLine)|Kod penceresindeimleç geçerli satır konumu.|
|Geçerli Sütun|$(Curcol)|Kod penceresindeimleç geçerli sütun konumu.|
|Geçerli Metin|$(CurText)|Seçili metin.|
|Hedef Yolu|$(TargetPath)|Oluşturulacak öğenin tam dosya adı (sürücü + yol + dosya adı).|
|Hedef Dizin|$(TargetDir)|Oluşturulacak öğenin dizini.|
|Hedef Adı|$(Hedef Ad)|Oluşturulacak öğenin dosya adı.|
|Hedef Uzantısı|$(TargetExt)|Oluşturulacak öğenin dosya adı uzantısı.|
|İkili Dizini|$(bindir)|Oluşturulmakta olan ikilinin son konumu (sürücü + yol olarak tanımlanır).|
|Proje Rehberi|$(ProjectDir)|Geçerli projenin dizini (sürücü + yol).|
|Proje Dosya Adı|$(ProjectFileName)|Geçerli projenin dosya adı (sürücü + yol + dosya adı).|
|Çözüm Rehberi|$(Çözümdür)|Geçerli çözümün dizini (sürücü + yol).|
|Çözüm Dosya Adı|$(SolutionFileName)|Geçerli çözümün dosya adı (sürücü + yol + dosya adı).|

> [!NOTE]
> IDE durum çubuğu, ekleme noktasının etkin Kod Düzenleyicisi'nde nerede bulunduğunu belirtmek **Code Editor**için **Geçerli Satır** ve **Geçerli Sütun** değişkenlerini görüntüler. **Geçerli Metin** değişkeni, o konumda seçilen metni veya kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.

- [C/C++ yapı araçları](/cpp/build/reference/c-cpp-build-tools)
