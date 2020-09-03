---
title: 'Nasıl yapılır: derleme çıkış dizinini değiştirme | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- output directory, changing
ms.assetid: a8333c89-afb2-4b1d-b2e2-9146da852402
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b665f5788d12c294e8ab7f55ecc63d183030a0ca
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72645428"
---
# <a name="how-to-change-the-build-output-directory"></a>Nasıl Yapılır: Yapı Çıktı Dizinini Değiştirme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Çıktının konumunu, projeniz tarafından oluşturulan yapılandırma bazında (hata ayıklama, yayın veya her ikisi için) belirtebilirsiniz.

> [!NOTE]
> Bir **Kurulum** projeniz varsa, bu makalenin sonundaki nota bakın.

## <a name="changing-the-build-output-directory"></a>Derleme çıkış dizinini değiştirme

#### <a name="to-change-the-build-output-directory"></a>Yapı çıkış dizinini değiştirmek için

1. Menü çubuğunda **Proje**, *appname* **özellikleri**' ni seçin. Ayrıca, **Çözüm Gezgini** proje düğümüne sağ tıklayıp **Özellikler**' i seçebilirsiniz.

2. Visual Basic projeniz varsa, **Derle** sekmesini seçin. Visual C# projeniz varsa, **derleme** sekmesini seçin. Bir C++ projeniz veya bir JavaScript projeniz varsa **genel** sekmesini seçin.

3. Üstteki yapılandırma açılır penceresinde çıkış dosyası konumunu değiştirmek istediğiniz yapılandırmayı (hata ayıklama, yayın veya tümü) seçin.

     Çıkış yolu girişini (Visual Basic**derleme çıkış yolunu** , Visual C++ **çıkış dizinini** , JavaScript ve C# ' deki **Çıkış yolunu** ) bulun. Proje diziniyle ilişkili yeni bir derleme çıkış dizini belirtin.

> [!NOTE]
> Bir kurulum projesinde, **Çıkış dosyası adı** kutusu, proje dosyalarının konumu değil yalnızca Setup.exe dosyasının konumunu değiştirir. Daha fazla bilgi için bkz. **derleme, yapılandırma özellikleri, dağıtım projesi özellikleri Iletişim kutusu**.

## <a name="see-also"></a>Ayrıca Bkz.
 [Derleme sayfası, proje Tasarımcısı (C#)](../ide/reference/build-page-project-designer-csharp.md) [genel özellik sayfası (proje)](https://msdn.microsoft.com/library/593b383c-cd0f-4dcd-ad65-9ec9b4b19c45) [derleme ve oluşturma](../ide/compiling-and-building-in-visual-studio.md)
