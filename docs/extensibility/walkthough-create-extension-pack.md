---
title: Uzantı Paketi Oluşturma
description: Uzantı Paketi Öğe Şablonu ile Uzantı Paketi oluşturma hakkında bilgi
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

Uzantı Paketi, birlikte yüklen kolay bir uzantı kümesidir. Uzantı Paketleri, sık kullanılan uzantılarınızı diğer kullanıcılarla kolayca paylaşmanıza veya belirli bir senaryo için bir uzantı kümesi paketlediğinize olanak sağlar.

## <a name="prerequisites"></a>Önkoşullar

Visual Studio 2015'te Visual Studio SDK, kurulumda isteğe bağlı bir Visual Studio olarak dahil edilir. VS SDK'yı daha sonra da yükleyebilirsiniz. Daha fazla bilgi için [bkz. Visual Studio SDK'sı yükleme.](../extensibility/installing-the-visual-studio-sdk.md)

Uzantı Paketi özelliği, Visual Studio 15.8 Preview 2'den başlayarak kullanılabilir.

## <a name="create-an-extension-with-an-extension-pack-item-template"></a>Uzantı Paketi öğe şablonuyla uzantı oluşturma

Uzantı Paketi öğe şablonu, birlikte yüklen kullanılabilir uzantı kümesine sahip bir Uzantı Paketi oluşturur.

1. Yeni **Project** iletişim kutusunda "vsix" araması ve **VSIX'i Project.** Bir **Project için**"Test Uzantısı Paketi" yazın. **Oluştur**’u seçin.

2. Giriş **Çözüm Gezgini** proje düğümüne sağ tıklayın ve Yeni Öğe **Ekle'yi**  >  **seçin.** Visual C# **Genişletilebilirlik düğümüne gidin ve** Uzantı **Paketi'ne gidin.** Varsayılan dosya adını (ExtensionPack1.cs) bırakın.

3. Aşağıdaki kodu içeren ExtensionPack1.vsext dosyası eklendi

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

4. Uzantı Paketi'ne dahil etmek için uzantının vsixid'leri markette [Visual Studio bulunabilir.](https://marketplace.visualstudio.com/) Dahil etmek istediğiniz uzantıyı bulun ve Kimliği **Kopyala'ya tıklayın.** Yukarıdaki dosyada var olan **vsixId'yi** güncelleştirebilirsiniz veya listeye başka bir uzantı ekleyebilirsiniz.

    ![Marketten VsixId kopyalama](media/vsixid-marketplace.png)

5. Projeyi derleme ve uzantınızı Market'e yükleme. Bkz. [Visual Studio yayımlama.](../extensibility/walkthrough-publishing-a-visual-studio-extension.md)

> [!NOTE]
> Bir Uzantı paketi yalnızca Market'te veya Özel [galeride Visual Studio](https://marketplace.visualstudio.com/) [uzantılar yükleyebilir.](../extensibility/how-to-create-an-atom-feed-for-a-private-gallery.md)

## <a name="install-the-extension-pack-from-the-visual-studio-marketplace"></a>Visual Studio Market'Visual Studio Yükleme

Artık uzantı yayımlanır ve uzantıyı Visual Studio orada test etmek için yükleyin.

::: moniker range="vs-2017"

1. Bu Visual Studio Araçlar menüsünde **Uzantılar** ve **Güncelleştirmeler'e tıklayın.**

::: moniker-end

::: moniker range=">=vs-2019"

1. Bu Visual Studio, **Uzantılar menüsünde Yönetilen** Uzantılar'a **tıklayın.**

::: moniker-end

2. **Çevrimiçi'ne** tıklayın ve "Test Uzantısı Paketi" araması yapabilirsiniz.

3. **İndir**’e tıklayın. Uzantı paketine dahil edilen uzantı ve uzantı listesi daha sonra yüklenmek üzere zamanlanmış olur.

4. Uzantıları Yönet iletişim kutusunun örnek bir Uzantı Paketi **indirme görünümü aşağıda verilmiştir.** Uzantı paketine dahil edilen uzantıların yalnızca bir listesini yüklemek isterseniz, Yükleme için Zamanlanmış içinde uzantı **listesini değiştirebilirsiniz.**

    ![Market'te Uzantı Paketi'ne indirme](media/vside-extensionpack.png)

5. Yükleme işlemini tamamlamak için tüm örnek örneklerini Visual Studio.

## <a name="remove-the-extension"></a>Uzantıyı kaldırma

Uzantıyı bilgisayarınızdan kaldırmak için:

::: moniker range="vs-2017"

1. Bu Visual Studio Araçlar menüsünde **Uzantılar** ve **Güncelleştirmeler'e tıklayın.**

::: moniker-end

::: moniker range=">=vs-2019"

1. Bu Visual Studio, **Uzantılar menüsünde Yönetilen** Uzantılar'a **tıklayın.**

::: moniker-end

2. Uzantı **Paketini Sına'yı seçin** ve ardından Kaldır'a **tıklayın.** Uzantı paketine dahil edilen uzantı ve uzantı listesi daha sonra kaldırılmak üzere zamanlanmış olur.

3. Kaldırma işlemini tamamlamak için tüm örnek örneklerini Visual Studio.
