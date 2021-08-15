---
title: Uzantı Paketi Oluşturma
description: Uzantı paketi öğe şablonuyla bir uzantı paketi oluşturmayı öğrenin
ms.custom: SEO-VS-2020
ms.date: 07/27/2018
ms.topic: tutorial
helpviewer_keywords:
- editors [Visual Studio SDK], new - extensions
ms.assetid: 5388EEBA-211D-4114-8CD9-70C899919F7E
author: leslierichardson95
ms.author: lerich
manager: Meng
ms.workload:
- vssdk
ms.openlocfilehash: a84647eef6fa81f55a02689b1adb584c21fd3565a22662e1e9d19b9f1bacb18f
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121335088"
---
# <a name="walkthrough-create-an-extension-pack"></a>İzlenecek yol: Uzantı Paketi Oluşturma

Uzantı paketi, birlikte yüklenebilen bir uzantılar kümesidir. Uzantı paketleri, sık kullandığınız uzantıları diğer kullanıcılarla kolayca paylaşmanıza veya belirli bir senaryo için bir dizi uzantıyı birlikte paketlemenize olanak tanır.

## <a name="prerequisites"></a>Önkoşullar

Visual Studio 2015 ' den başlayarak Visual Studio SDK Visual Studio kurulum 'da isteğe bağlı bir özellik olarak eklenmiştir. VS SDK ' yı daha sonra da yükleyebilirsiniz. daha fazla bilgi için bkz. [Visual Studio SDK 'yı yükleme](../extensibility/installing-the-visual-studio-sdk.md).

uzantı paketi özelliği Visual Studio 15,8 Preview 2 ' den başlayarak kullanılabilir.

## <a name="create-an-extension-with-an-extension-pack-item-template"></a>Uzantı paketi öğe şablonuyla uzantı oluşturma

Uzantı paketi öğe şablonu, birlikte yüklenebilen uzantılar kümesine sahip bir uzantı paketi oluşturur.

1. **yeni Project** iletişim kutusunda, "vsıx" araması yapın ve **vsıx Project**' i seçin. **Project adı** için "Test uzantı paketi" yazın. **Oluştur**’u seçin.

2. **Çözüm Gezgini**, proje düğümüne sağ tıklayın ve   >  **Yeni öğe** Ekle ' yi seçin. Visual C# **genişletilebilirlik** düğümüne gidin ve **Uzantı paketi**' ni seçin. Varsayılan dosya adını (ExtensionPack1. cs) bırakın.

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

4. uzantı paketine dahil edilecek uzantının valtıd 'si [Visual Studio marketi](https://marketplace.visualstudio.com/)'nde bulunabilir. Dahil etmek istediğiniz uzantıyı bulun ve **kopya kimliği**' ne tıklayın. Yukarıdaki dosyadaki var olan **Valtıd** 'yi güncelleştirebilir veya listeye başka bir uzantı ekleyebilirsiniz.

    ![Marketten Valtıd kopyalama](media/vsixid-marketplace.png)

5. Projeyi derleyin ve uzantınızı Market 'e yükleyin. bkz. [Visual Studio uzantısı yayımlama](../extensibility/walkthrough-publishing-a-visual-studio-extension.md).

> [!NOTE]
> bir uzantı paketi yalnızca [Visual Studio marketi](https://marketplace.visualstudio.com/) veya [özel galeride](../extensibility/how-to-create-an-atom-feed-for-a-private-gallery.md)bulunan uzantıları yükleyebilir.

## <a name="install-the-extension-pack-from-the-visual-studio-marketplace"></a>Visual Studio marketi 'nden uzantı paketini yükler

artık uzantı yayımlandığına göre Visual Studio yükleyip test edin.

::: moniker range="vs-2017"

1. Visual Studio, **araçlar** menüsünde **uzantılar ve güncelleştirmeler**' e tıklayın.

::: moniker-end

::: moniker range=">=vs-2019"

1. Visual Studio, **uzantılar** menüsünde, **yönetilen uzantılar**' a tıklayın.

::: moniker-end

2. **Çevrimiçi** ' e tıklayın ve ardından "test Uzantı paketi" ni arayın.

3. **İndir**’e tıklayın. Uzantı ve uzantı paketine dahil olan uzantıların listesi, daha sonra yüklenmek üzere zamanlanır.

4. **Uzantıları Yönet** iletişim kutusunun örnek Uzantı paketi indirme görünümü aşağıda verilmiştir. Uzantı paketine dahil edilen uzantılardan yalnızca bazılarını yüklemeyi tercih ediyorsanız, ' ın **yüklenmek üzere zamanlanan** uzantı listesini değiştirebilirsiniz.

    ![Uzantı paketini Market 'ten indirin](media/vside-extensionpack.png)

5. Yüklemeyi gerçekleştirmek için Visual Studio tüm örneklerini kapatın.

## <a name="remove-the-extension"></a>Uzantıyı kaldırma

Uzantıyı bilgisayarınızdan kaldırmak için:

::: moniker range="vs-2017"

1. Visual Studio, **araçlar** menüsünde **uzantılar ve güncelleştirmeler**' e tıklayın.

::: moniker-end

::: moniker range=">=vs-2019"

1. Visual Studio, **uzantılar** menüsünde, **yönetilen uzantılar**' a tıklayın.

::: moniker-end

2. **Test Uzantı paketi** ' ni seçin ve ardından **Kaldır**' a tıklayın. Uzantı paketinde bulunan uzantı ve uzantı listesi, kaldırma işlemi için zamanlanır.

3. Kaldırma işlemini gerçekleştirmek için Visual Studio tüm örneklerini kapatın.
