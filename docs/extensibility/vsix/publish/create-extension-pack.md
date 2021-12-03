---
title: Uzantı paketi oluşturma
description: Sık kullanılan uzantılarınızı kolayca başkalarla paylaşmak veya bir uzantı kümesi birlikte paketlemek için bir uzantı paketi oluşturun.
ms.date: 12/01/2021
ms.topic: conceptual
author: madskristensen
ms.author: madsk
manager: pchapman
ms.prod: visual-studio-windows
ms.technology: vs-ide-sdk
ms.custom: cookbook
ms.openlocfilehash: 57dd6c11b75725e13d52e120f547ed47774e41a5
ms.sourcegitcommit: a149b3a034bb555ad217656c0ec8bc1672b1e215
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2021
ms.locfileid: "133516627"
---
# <a name="create-an-extension-pack"></a>Uzantı Paketi Oluşturma

Bu makalede, uzantı paketinin nasıl oluşturularak ilgili bilgi ve süreler açıklanmıştır. Uzantı Paketi, birlikte yüklen kolay bir uzantı kümesidir. Uzantı Paketleri, sık kullanılan uzantılarınızı diğer kullanıcılarla kolayca paylaşmanıza veya belirli bir senaryo için bir uzantı kümesi paketlediğinize olanak sağlar.

Aşağıdaki videoda Uzantı Paketlerinin nasıl oluşturularak ilgili bilgiler ve bilgiler yer almaktadır.
> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWP8KA]

## <a name="create-from-project-template"></a>Proje şablonundan oluşturma
Uzantı Paketi proje şablonu, birlikte yüklen kullanılabilir uzantı kümesine sahip bir Uzantı Paketi oluşturur.

Yeni Hizmet **Project** iletişim kutusunda uzantıyı *arayın* ve Uzantı **Paketi'yi seçin.** Ad **Project** Test Uzantısı *Paketi girin.* **Oluştur**’u seçin.

Visual Studio, projeyi Çözüm Gezgini **extensions.vsext** dosyasını düzenleyicide açar.

```json
{
  "version": "1.0.0.0",
  "extensions": [
    {
      "vsixId": "OneDarkPro.e1e706e2-05d3-4da9-8754-652cd8ab65f4",
      "name": "One Dark Pro"
    },
    {
      "vsixId": "7fa839e2-b938-4b1c-9277-edaebe6fdeb5",
      "name": "Winter is Coming"
    }
  ]
}
```

## <a name="add-to-existing-extension"></a>Mevcut uzantıya ekleme
Yeni Çözüm Gezgini proje düğümüne sağ tıklayın ve Yeni Öğe'ye **>'yi seçin.** **Visual C# Genişletilebilirlik düğümüne gidin ve** Uzantı **Paketi'ne gidin.** Varsayılan dosya adını (ExtensionPack1.cs) bırakın.

Projenizin kökünde yer alan .vsext dosyası, projeyi bir uzantı paketine dönüştüren dosyadır. Derleme Eylemi'nin İçerik olarak *ve* *VSIX'e* Dahil Etmek'in aşağıda gösterildiği gibi *True* olarak ayarlanmış olduğundan emin olun. 

![VSIX'e dahil edin](../media/include-in-vsix.png)
