---
title: Uzantı Paketi Öğe Şablonu ile Uzatma Paketi Oluşturma | Microsoft Dokümanlar
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
ms.openlocfilehash: fa1c141e18a3870eaad4b155d816e30ee207f45d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697745"
---
# <a name="walkthrough-create-an-extension-pack"></a>İzlenecek yol: Uzantı Paketi Oluşturma

Uzatma Paketi, birlikte yüklenebilen bir uzantı kümesidir. Uzantı Paketleri, en sevdiğiniz uzantıları diğer kullanıcılarla kolayca paylaşmanızı veya belirli bir senaryo için bir dizi uzantıyı bir araya toplamanızı sağlar.

## <a name="prerequisites"></a>Ön koşullar

Visual Studio 2015'ten itibaren Visual Studio SDK, Visual Studio kurulumunda isteğe bağlı bir özellik olarak yer almaktadır. VS SDK'yı daha sonra da yükleyebilirsiniz. Daha fazla bilgi için Visual [Studio SDK'yı yükleme ye](../extensibility/installing-the-visual-studio-sdk.md)bakın.

Uzatma Paketi özelliği Visual Studio 15.8 Preview 2'den başlayarak kullanılabilir.

## <a name="create-an-extension-with-an-extension-pack-item-template"></a>Uzantı Paketi öğesi şablonuyla uzantı oluşturma

Uzantı Paketi öğesi şablonu, birlikte yüklenebilen uzantılar kümesine sahip bir Uzantı Paketi oluşturur.

1. Yeni **Proje** iletişim kutusunda "vsix" araması yapın ve **VSIX Project'i**seçin. **Proje adı için**"Test Uzantı Paketi" yazın. **Oluştur'u**seçin.

2. Çözüm **Gezgini'nde**proje düğümüne sağ tıklayın ve**Yeni Öğe** **Ekle'yi** > seçin. Visual C# **Genişletilebilirlik** düğümüne gidin ve **Uzantı Paketi'ni**seçin. Varsayılan dosya adını bırakın (ExtensionPack1.cs).

3. ExtensionPack1.vsext dosyası aşağıdaki kodu içeren eklenir

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

4. Uzatma Paketi'ne dahil etmek için uzantı vsixid [Visual Studio Marketplace](https://marketplace.visualstudio.com/)bulunabilir. Eklemek istediğiniz uzantıyı bulun ve **Kimliği Kopyala'ya**tıklayın. Yukarıdaki dosyadaki mevcut **vsixId'i** güncelleyebilir veya listeye başka bir uzantı ekleyebilirsiniz.

    ![Pazardan VsixId Kopyala](media/vsixid-marketplace.png)

5. Projeyi oluşturun ve uzantınızı Market'e yükleyin. Bkz. [Görsel Stüdyo uzantısı yayımlama.](../extensibility/walkthrough-publishing-a-visual-studio-extension.md)

> [!NOTE]
> Uzatma paketi yalnızca [Visual Studio Marketplace](https://marketplace.visualstudio.com/) veya Private [gallery'de](../extensibility/how-to-create-an-atom-feed-for-a-private-gallery.md)bulunan uzantıları yükleyebilir.

## <a name="install-the-extension-pack-from-the-visual-studio-marketplace"></a>Uzatma Paketini Visual Studio Marketplace'ten yükleyin

Şimdi uzantısı yayımlanır, Visual Studio yükleyin ve orada test edin.

::: moniker range="vs-2017"

1. Visual Studio'da, **Araçlar** menüsünde **Uzantılar ve Güncellemeler'i**tıklatın.

::: moniker-end

::: moniker range=">=vs-2019"

1. Visual Studio'da, **Uzantılar** menüsünde **Yönetilen Uzantılar'ı**tıklatın.

::: moniker-end

2. **Çevrimiçi'yi** tıklatın ve ardından "Test Uzatma Paketi"ni arayın.

3. **İndir'i**tıklatın. Uzantı paketive uzantılistesi daha sonra yüklemek için zamanlanır.

4. Aşağıda, **Uzantıları Yönet** iletişim kutusunun örnek bir Uzantı Paketi indirme görünümü verilmiştir. Uzantı paketine yalnızca bazı uzantıları yüklemeyi tercih ederseniz, **Zamanlanmış Yükleme için**uzantı listesini değiştirebilirsiniz.

    ![Marketplace'ten Uzantı Paketi İndir](media/vside-extensionpack.png)

5. Yüklemeyi tamamlamak için Visual Studio'nun tüm örneklerini kapatın.

## <a name="remove-the-extension"></a>Uzantıyı kaldırma

Uzantıyı bilgisayarınızdan kaldırmak için:

::: moniker range="vs-2017"

1. Visual Studio'da, **Araçlar** menüsünde **Uzantılar ve Güncellemeler'i**tıklatın.

::: moniker-end

::: moniker range=">=vs-2019"

1. Visual Studio'da, **Uzantılar** menüsünde **Yönetilen Uzantılar'ı**tıklatın.

::: moniker-end

2. **Test Uzantısı Paketi'ni** seçin ve **ardından Kaldır'ı**tıklatın. Uzantı paketive uzantılistesi daha sonra kaldırılacak şekilde zamanlanır.

3. Yüklemeyi tamamlamak için Visual Studio'nun tüm örneklerini kapatın.
