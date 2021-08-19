---
title: Dış araçları yönetme
description: Araçlar menüsü aracılığıyla erişebileceğiniz yeni dış araçlar ekleme ve yönetme hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/20/2017
ms.topic: conceptual
f1_keywords:
- vs.externaltools
helpviewer_keywords:
- external tools [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 9b7db6b407c92aee112301cedd34f93b6b2a91fc
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122085929"
---
# <a name="manage-external-tools"></a>Dış araçları yönetme

**araçlar** menüsünü kullanarak Visual Studio içinden dış araçlar çağırabilirsiniz. **Araçlar** menüsünde birkaç varsayılan araç mevcuttur ve kendi kendinize ait diğer yürütülebilir dosyaları ekleyerek menüyü özelleştirebilirsiniz.

## <a name="tools-available-on-the-tools-menu"></a>Araçlar menüsünde bulunan araçlar

**Araçlar** menüsü aşağıdakiler dahil olmak üzere çeşitli yerleşik komutlar içerir:

::: moniker range="vs-2017"

* [Visual Studio uzantılarını yönetmeye](finding-and-using-visual-studio-extensions.md) yönelik **uzantılar ve güncelleştirmeler**
* [Kod parçacıklarını düzenlemek](code-snippets.md) Için **kod parçacıkları Yöneticisi**
* [Menüleri ve araç çubuklarını özelleştirmek](how-to-customize-menus-and-toolbars-in-visual-studio.md) için **özelleştirin**
* [Visual Studio ıde ve diğer araçlar için çeşitli farklı seçenekler ayarlama](reference/options-dialog-box-visual-studio.md) **seçenekleri**

::: moniker-end

::: moniker range=">=vs-2019"

* [Kod parçacıklarını düzenlemek](code-snippets.md) Için **kod parçacıkları Yöneticisi**
* [Menüleri ve araç çubuklarını özelleştirmek](how-to-customize-menus-and-toolbars-in-visual-studio.md) için **özelleştirin**
* [Visual Studio ıde ve diğer araçlar için çeşitli farklı seçenekler ayarlama](reference/options-dialog-box-visual-studio.md) **seçenekleri**

::: moniker-end

## <a name="add-new-tools-to-the-tools-menu"></a>Araçlar menüsüne yeni araçlar ekleme

**Araçlar** menüsünde görünecek bir dış araç ekleyebilirsiniz.

1. **Araçlar** dış araçları ' nı seçerek **dış araçlar** iletişim kutusunu açın  >  .

1. **Ekle**' ye tıklayın ve ardından bilgileri girin. örneğin, aşağıdaki giriş, **Windows gezgini** 'nin şu anda Visual Studio açık olan dosya dizininde açılmasını sağlar:

   * Başlığın `Open File Location`

   * Komutundaki `explorer.exe`

   * Değişkenlerinden `/root, "$(ItemDir)"`

   ![Dış Araçlar iletişim kutusu](media/external-tools-dialog.png)

Aşağıda, dış bir araç tanımlarken kullanılabilecek bağımsız değişkenlerin tam bir listesi verilmiştir:

|Name|Bağımsız Değişken|Açıklama|
|----------|--------------|-----------------|
|Öğe yolu|$ (ItemPath)|Geçerli dosyanın (sürücü + yol + dosya adı) tüm dosya adı.|
|Öğe dizini|$ (Itemdır)|Geçerli dosyanın dizini (sürücü + yol).|
|Öğe dosyası adı|$ (Itemfilename)|Geçerli dosyanın (dosya adı) dosya adı.|
|Öğe uzantısı|$ (ItemExt)|Geçerli dosyanın dosya adı uzantısı.|
|Geçerli satır|$ (CurLine)|İmlecin kod penceresindeki geçerli satır konumu.|
|Geçerli sütun|$ (CurCol)|İmlecin kod penceresindeki geçerli sütun konumu.|
|Geçerli metin|$ (CurText)|Seçilen metin.|
|Hedef yol|$ (TargetPath)|Oluşturulacak öğenin tamamı dosya adı (sürücü + yol + dosya adı).|
|Hedef Dizin|$ (TARGETDIR)|Oluşturulacak öğenin dizini.|
|Hedef Adı|$ (TargetName)|Oluşturulacak öğenin dosya adı.|
|Hedef uzantısı|$ (TargetExt)|Oluşturulacak öğenin dosya adı uzantısı.|
|İkili dizin|$ (BinDir)|Oluşturulmakta olan ikilinin son konumu (sürücü + yol olarak tanımlanır).|
|Project Dizinden|$ (ProjectDir)|Geçerli projenin dizini (sürücü + yol).|
|Project Dosya adı|$ (ProjectFileName)|Geçerli projenin dosya adı (sürücü + yol + dosya adı).|
|Çözüm dizini|$ (SolutionDir)|Geçerli çözümün dizini (sürücü + yol).|
|Çözüm dosyası adı|$ (SolutionFileName)|Geçerli çözümün dosya adı (sürücü + yol + dosya adı).|

> [!NOTE]
> IDE durum çubuğu, ekleme noktasının etkin **kod düzenleyicisinde** nerede olduğunu göstermek Için **geçerli satırı** ve **Geçerli sütun** değişkenlerini görüntüler. **Geçerli metin** değişkeni, bu konumda seçili olan metni veya kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.

- [C/C++ derleme araçları](/cpp/build/reference/c-cpp-build-tools)
