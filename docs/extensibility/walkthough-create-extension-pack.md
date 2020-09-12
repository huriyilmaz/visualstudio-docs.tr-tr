---
title: Uzantı Paketi Oluşturma
description: Uzantı paketi öğe şablonuyla bir uzantı paketi oluşturmayı öğrenin
ms.custom: SEO-VS-2020
ms.date: 07/27/2018
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - extensions
ms.assetid: 5388EEBA-211D-4114-8CD9-70C899919F7E
author: acangialosi
ms.author: anthc
manager: Meng
ms.workload:
- vssdk
ms.openlocfilehash: c959660b920abc18be70b228fa6b40de1ab585f8
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/11/2020
ms.locfileid: "90037666"
---
# <a name="walkthrough-create-an-extension-pack"></a>İzlenecek yol: Uzantı Paketi Oluşturma

Uzantı paketi, birlikte yüklenebilen bir uzantılar kümesidir. Uzantı paketleri, sık kullandığınız uzantıları diğer kullanıcılarla kolayca paylaşmanıza veya belirli bir senaryo için bir dizi uzantıyı birlikte paketlemenize olanak tanır.

## <a name="prerequisites"></a>Ön koşullar

Visual Studio 2015 ' den başlayarak Visual Studio SDK, Visual Studio Kurulumu 'nda isteğe bağlı bir özellik olarak eklenmiştir. VS SDK ' yı daha sonra da yükleyebilirsiniz. Daha fazla bilgi için bkz. [Visual Studio SDK 'Yı yükleme](../extensibility/installing-the-visual-studio-sdk.md).

Uzantı paketi özelliği Visual Studio 15,8 Preview 2 ' den itibaren kullanılabilir.

## <a name="create-an-extension-with-an-extension-pack-item-template"></a>Uzantı paketi öğe şablonuyla uzantı oluşturma

Uzantı paketi öğe şablonu, birlikte yüklenebilen uzantılar kümesine sahip bir uzantı paketi oluşturur.

1. **Yeni proje** iletişim kutusunda, "VSIX" araması yapın ve **VSIX projesi**' ni seçin. **Proje adı**Için "test Uzantı paketi" yazın. **Oluştur**’u seçin.

2. **Çözüm Gezgini**, proje düğümüne sağ tıklayın ve **Add**  >  **Yeni öğe**Ekle ' yi seçin. Visual C# **genişletilebilirlik** düğümüne gidin ve **Uzantı paketi**' ni seçin. Varsayılan dosya adını (ExtensionPack1.cs) bırakın.

3. Aşağıdaki kodu içeren ExtensionPack1. vsext dosyası eklenir

   ```json
   {
    "id": "ExtensionPack1",
    "name": "ExtensionPack1",
    "description": "Read about creating extension packs at https://aka.ms/vsextpack",
    "version": "1.0.0.0",
    "extensions": [  // List of extensions that are included in the Extension Pack.
      {
        "vsixId": "41858b2d-ff0b-4a43-80b0-f1b2d6084935", // The vsix id of the extension you want to   include.
        "name": "AlignAssignments"
      },
      {
          "vsixId": "42374550-426a-400e-96f9-237682e8dea6",
        "name": "CopyAsHtml"
      }
    ]
   }
   ```

4. Uzantı paketine dahil edilecek uzantının valtıd 'si [Visual Studio Market](https://marketplace.visualstudio.com/)bulunabilir. Dahil etmek istediğiniz uzantıyı bulun ve **kopya kimliği**' ne tıklayın. Yukarıdaki dosyadaki var olan **Valtıd** 'yi güncelleştirebilir veya listeye başka bir uzantı ekleyebilirsiniz.

    ![Marketten Valtıd kopyalama](media/vsixid-marketplace.png)

5. Projeyi derleyin ve uzantınızı Market 'e yükleyin. Bkz. [Visual Studio uzantısı yayımlama](../extensibility/walkthrough-publishing-a-visual-studio-extension.md).

> [!NOTE]
> Bir uzantı paketi yalnızca [Visual Studio Market](https://marketplace.visualstudio.com/) veya [özel galeride](../extensibility/how-to-create-an-atom-feed-for-a-private-gallery.md)bulunan uzantıları yükleyebilir.

## <a name="install-the-extension-pack-from-the-visual-studio-marketplace"></a>Visual Studio Market uzantı paketini yükler

Artık uzantı yayımlandığına göre, Visual Studio 'Ya yükleyip test edin.

::: moniker range="vs-2017"

1. Visual Studio 'da, **Araçlar** menüsünde **Uzantılar ve güncelleştirmeler**' e tıklayın.

::: moniker-end

::: moniker range=">=vs-2019"

1. Visual Studio 'da, **Uzantılar** menüsünde, **yönetilen uzantılar**' a tıklayın.

::: moniker-end

2. **Çevrimiçi** ' e tıklayın ve ardından "test Uzantı paketi" ni arayın.

3. **İndir**'e tıklayın. Uzantı ve uzantı paketine dahil olan uzantıların listesi, daha sonra yüklenmek üzere zamanlanır.

4. **Uzantıları Yönet** iletişim kutusunun örnek Uzantı paketi indirme görünümü aşağıda verilmiştir. Uzantı paketine dahil edilen uzantılardan yalnızca bazılarını yüklemeyi tercih ediyorsanız, ' ın **yüklenmek üzere zamanlanan**uzantı listesini değiştirebilirsiniz.

    ![Uzantı paketini Market 'ten indirin](media/vside-extensionpack.png)

5. Yüklemeyi gerçekleştirmek için Visual Studio 'nun tüm örneklerini kapatın.

## <a name="remove-the-extension"></a>Uzantıyı kaldırma

Uzantıyı bilgisayarınızdan kaldırmak için:

::: moniker range="vs-2017"

1. Visual Studio 'da, **Araçlar** menüsünde **Uzantılar ve güncelleştirmeler**' e tıklayın.

::: moniker-end

::: moniker range=">=vs-2019"

1. Visual Studio 'da, **Uzantılar** menüsünde, **yönetilen uzantılar**' a tıklayın.

::: moniker-end

2. **Test Uzantı paketi** ' ni seçin ve ardından **Kaldır**' a tıklayın. Uzantı paketinde bulunan uzantı ve uzantı listesi, kaldırma işlemi için zamanlanır.

3. Kaldırma işlemini gerçekleştirmek için Visual Studio 'nun tüm örneklerini kapatın.
