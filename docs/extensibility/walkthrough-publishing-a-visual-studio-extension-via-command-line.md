---
title: Uzantı komut satırını kullanarak Yayımla
description: bir uzantıyı Visual Studio marketi 'nde yayımlamak için komut satırını kullanarak geliştiricilerin yeni ve güncelleştirilmiş uzantılara gözatmasına olanak tanır.
ms.custom: SEO-VS-2020
ms.date: 07/12/2018
ms.topic: how-to
helpviewer_keywords:
- publishing extensions
- extension, publishing
ms.assetid: 6ff9efc4-919d-4071-a80d-6dbdd2ceb2f8
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: b7cac2a9f5aa59bb3305f96340a987569e18a1a5
ms.sourcegitcommit: 23b0ef3815833426933ff6491271034658683f9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/02/2022
ms.locfileid: "137983825"
---
# <a name="walkthrough-publishing-a-visual-studio-extension-via-command-line"></a>izlenecek yol: komut satırı aracılığıyla Visual Studio uzantısı yayımlama

bu izlenecek yol, komut satırını kullanarak Visual Studio marketi 'nde bir Visual Studio uzantısının nasıl yayımlanacağını gösterir. Uzantınızı Market 'e eklediğinizde, geliştiriciler [**uzantıları ve güncelleştirmeler**](../ide/finding-and-using-visual-studio-extensions.md) iletişim kutusunu kullanarak yeni ve güncelleştirilmiş uzantılara gözatabilirler.

VsixPublisher.exe, market 'e Visual Studio uzantıları yayımlamaya yönelik komut satırı aracıdır. $ {VSInstallDir} \VSSDK\VisualStudioIntegration\Tools\Bin\VsixPublisher.exe adresinden erişilebilir. Bu araçtaki komutlar şunlardır: **Publish**, **deletepublisher**, **deleteextension**, **login**, **Logout**.

## <a name="commands"></a>Komutlar

### <a name="publish"></a>publish

Market 'e bir uzantı yayımlar. Uzantı bir VSIX, bir exe/MSI dosyası ya da bir bağlantı olabilir. Aynı sürüme sahip uzantı zaten varsa, uzantının üzerine yazar. Uzantı yoksa, yeni bir uzantı oluşturacaktır.

|Komut seçenekleri |Description |
|---------|---------|
|Yük (gerekli) | Yayımlanacak yükün yolu veya "daha fazla bilgi URL 'SI" olarak kullanılacak bir bağlantı. |
|publishManifest (gerekli) | Kullanılacak yayımlama bildirimi dosyasının yolu. |
|ıgnoreuyarılarla | Uzantı yayımlanırken yoksayılacak uyarıların listesi. Bu uyarılar, bir uzantı yayımlarken komut satırı iletileri olarak gösterilir. (örneğin, "VSIXValidatorWarning01, VSIXValidatorWarning02")
|personalAccessToken | Yayımcının kimliğini doğrulamak için kullanılan kişisel erişim belirteci (PAT). Sağlanmazsa, PAT oturum açmış kullanıcılardan elde edilir. |

```
VsixPublisher.exe publish -payload "{path to vsix}" -publishManifest "{path to vs-publish.json}" -ignoreWarnings "VSIXValidatorWarning01,VSIXValidatorWarning02"
```

### <a name="deletepublisher"></a>deletePublisher

Market 'teki bir yayımcıyı siler.

|Komut seçenekleri |Description |
|---------|---------|
|publisherName (gerekli) | Yayımcının adı (örneğin, tanımlayıcı). |
|personalAccessToken (gerekli) | Yayımcının kimliğini doğrulamak için kullanılan kişisel erişim belirteci. |

```
VsixPublisher.exe deletePublisher -publisherName "{Publisher Name}" -personalAccessToken "{Personal Access Token}"
```

### <a name="deleteextension"></a>deleteExtension

Marketten bir uzantıyı siler.

|Komut seçenekleri |Description |
|---------|---------|
|extensionName (gerekli) | Silinecek uzantının adı. |
|publisherName (gerekli) | Yayımcının adı (örneğin, tanımlayıcı). |
|personalAccessToken | Yayımcının kimliğini doğrulamak için kullanılan kişisel erişim belirteci. Sağlanmazsa, Pat oturum açmış kullanıcılardan elde edilir. |

```
VsixPublisher.exe deleteExtension -extensionName "{Extension Name}" -publisherName "{Publisher Name}"
```

### <a name="login"></a>oturum aç

Bir yayımcıyı makineye kaydeder.

|Komut seçenekleri |Description |
|---------|---------|
|personalAccessToken (gerekli | Yayımcının kimliğini doğrulamak için kullanılan kişisel erişim belirteci. |
|publisherName (gerekli) | Yayımcının adı (örneğin, tanımlayıcı). |
|yazılacak | Mevcut bir yayımcının yeni kişisel erişim belirteci ile üzerine yazılması gerektiğini belirtir. |

```
VsixPublisher.exe login -personalAccessToken "{Personal Access Token}" -publisherName "{Publisher Name}"
```

### <a name="logout"></a>logout

Makinenin bir yayımcısını günlüğe kaydeder.

|Komut seçenekleri |Description |
|---------|---------|
|publisherName (gerekli) | Yayımcının adı (örneğin, tanımlayıcı). |
|ıgnoremissingpublisher | Belirtilen yayımcı zaten oturum açmadıysa aracın hata olmaması gerektiğini belirtir. |

```
VsixPublisher.exe logout -publisherName "{Publisher Name}"
```

### <a name="createpublisher"></a>createPublisher
> [!Caution]
> Bu komut artık kullanılamıyor. [Visual Studio marketi](https://marketplace.visualstudio.com/manage/publishers)' ne giderek yeni bir yayımcı oluşturabilirsiniz.

## <a name="publishmanifest-file"></a>publishManifest dosyası

PublishManifest dosyası **Publish** komutu tarafından kullanılır. Market 'in bilmeleri gereken uzantıya ilişkin tüm meta verileri temsil eder. Karşıya yüklenen uzantı bir VSıX uzantısından sonra, "Identity" özelliği yalnızca "InternalName" kümesine sahip olmalıdır. Bunun nedeni, "kimlik" özelliklerinin geri kalanının valtmanifest dosyasından üretilemidir. Uzantı bir MSI/exe veya bir bağlantı uzantısı ise, kullanıcının "Identity" özelliğinde gerekli alanları sağlaması gerekir. Bildirimin geri kalanı Market 'e özgü bilgiler içerir (örneğin, soru&A 'nın etkin olup olmadığı, vb.).

VSıX uzantısı publishManifest dosyası örneği:

```json
{
    "$schema": "http://json.schemastore.org/vsix-publish",
    "categories": [ "build", "coding" ],  // The categories of the extension. Between 1 and 3 categories are required.
    "identity": {
        "internalName": "MyVsixExtension" // If not specified, we try to generate the name from the display name of the extension in the vsixmanifest file.
                                            // Required if the display name is not the actual name of the extension.
    },
    "overview": "overview.md",            // Path to the "readme" file that gets uploaded to the Marketplace. Required.
    "priceCategory": "free",              // Either "free", "trial", or "paid". Defaults to "free".
    "publisher": "MyPublisherName",       // The name of the publisher. Required.
    "private": false,                     // Specifies whether or not the extension should be public when uploaded. Defaults to false.
    "qna": true,                          // Specifies whether or not the extension should have a Q&A section. Defaults to true.
    "repo": "https://github.com/MyPublisherName/MyVsixExtension" // Not required.
}
```

MSI/EXE veya LINK publishManifest dosyası örneği:

```json
{
    "$schema": "http://json.schemastore.org/vsix-publish",
    "categories": [ "build", "coding" ],
    "identity": {
        "description": "My extension.", // The description of the extension. Required for non-vsix extensions.
        "displayName": "My Extension",  // The display name of the extension. Required for non-vsix extensions.
        "icon": "\\path\\to\\icon.ico", // The path to an icon file (can be relative to the json file location). Required for non-vsix extensions.
        "installTargets": [             // The installation targets for the extension. Required for non-vsix extensions.
            {
                "sku": "Microsoft.VisualStudio.Community",
                "version": "[10.0, 16.0)"
            }
        ],
        "internalName": "MyExtension",
        "language": "en-US",            // The default language id of the extension. Can be in the "1033" or "en-US" format. Required for non-vsix extensions.
        "tags": [ "tag1", "tag2" ],     // The tags for the extension. Not required.
        "version": "3.7.0",             // The version of the extension. Required for non-vsix extensions.
        "vsixId": "MyExtension",        // The vsix id of the extension. Not required but useful for showing updates to installed extensions.
    },
    "overview": "overview.md",
    "priceCategory": "free",
    "publisher": "MyPublisherName",
    "private": false,
    "qna": true,
    "repo": "https://github.com/MyPublisherName/MyVsixExtension"
}
```

## <a name="asset-files"></a>Varlık dosyaları

Varlık dosyaları, Benioku dosyasındaki görüntüler gibi ekleme işlemleri için belirtilebilir. Örneğin, bir uzantının aşağıdaki "genel bakış" Marku belgesi varsa:

```markdown
TestExtension
...
This is test extension.
![Test logo](images/testlogo.png "Test logo")
```

Önceki örnekteki "resimleri/testlogo.png" çözümlemek için, bir Kullanıcı aşağıdaki gibi yayımlama bildiriminde "assetFiles" sunabilir:

```json
{
    "assetFiles": [
        {
            "pathOnDisk": "\\path\\to\\logo.png",
            "targetPath": "images/logo.png"
        }
    ],
    // other required fields
}
```

## <a name="publishing-walkthrough"></a>Yayımlama Kılavuzu

### <a name="prerequisites"></a>Önkoşullar

bu yönergeyi izlemek için Visual Studio SDK 'sını yüklemelisiniz. daha fazla bilgi için bkz. [Visual Studio SDK 'yı yükleme](../extensibility/installing-the-visual-studio-sdk.md).

### <a name="create-a-visual-studio-extension"></a>Visual Studio uzantısı oluşturma

Bu durumda, varsayılan VSPackage uzantısını kullanacağız, ancak her uzantı türü için aynı adımlar geçerlidir.

1. Bir menü komutuna sahip "TestPublish" adlı C# dilinde VSPackage oluşturun. Daha fazla bilgi için, bkz. [Ilk uzantınızı oluşturma: Merhaba Dünya](../extensibility/extensibility-hello-world.md).

### <a name="package-your-extension"></a>Uzantınızı paketleyin

1. Valtmanifest uzantısını ürün adı, yazarı ve sürümü hakkındaki doğru bilgilerle güncelleştirin.

   ![Uzantı valtbildirimini Güncelleştir](media/update-extension-vsixmanifest.png)

2. Uzantınızı **yayın** modunda derleyin. Şimdi uzantınızın, \bin\Release klasöründe bir VSıX olarak paketlenmesi gerekir.

3. Yüklemeyi doğrulamak için VSıX 'e çift tıklayabilirsiniz.

### <a name="test-the-extension"></a>Uzantıyı test etme

 Uzantıyı dağıtmadan önce, Visual Studio deneysel örneğine doğru yüklendiğinden emin olmak için oluşturun ve test edin.

1. Visual Studio, hata ayıklamayı başlatın. Visual Studio deneysel bir örneğini açmak için.

2. Deneysel örnekte, **Araçlar** menüsüne gidin ve **Uzantılar ve güncelleştirmeler...** öğesine tıklayın. TestPublish uzantısı Orta bölmede görünmelidir ve etkinleştirilmelidir.

3. **Araçlar** menüsünde, test komutunu görtığınızdan emin olun.

### <a name="publish-the-extension-to-the-marketplace-via-command-line"></a>Uzantıyı komut satırı aracılığıyla Market'te yayımlama

1. Uzantının Yayın sürümünü ve güncel olduğundan emin olun.

2. publishmanifest.json ve overview.md emin olun.

3. Komut satırı açın ve ${VSInstallDir}\VSSDK\VisualStudioIntegration\Tools\Bin\ dizinine gidin.

4. Yeni bir uzantı yayımlamak için aşağıdaki komutu kullanın:

   ```
   VsixPublisher.exe publish -payload "{Path to vsix file}"  -publishManifest "{path to publishManifest file}"  -personalAccessToken "{Personal Access Token that is used to authenticate the publisher. If not provided, the pat is acquired from the logged-in users.}"
   ```

5. Uzantı başarıyla yayımlanırken aşağıdaki komut satırı iletisini alırsınız:

   ```
   Uploaded 'MyVsixExtension' to the Marketplace.
   ```

6. Visual Studio Market'e giderek yayımladığınız [yeni uzantıyı doğruabilirsiniz](https://marketplace.visualstudio.com/)

### <a name="install-the-extension-from-the-visual-studio-marketplace"></a>Visual Studio Market'Visual Studio yükleme

Artık uzantı yayımlanır ve uzantıyı Visual Studio test etmek için bu uzantıyı yükleyin.

1. Bu Visual Studio Araçlar menüsünde **Uzantılar** ve Güncelleştirmeler... **seçeneğine tıklayın**.

2. **Çevrimiçi'ne** tıklayın ve TestPublish araması için arama.

3. **İndir**’e tıklayın. Uzantı daha sonra yüklenmek üzere zamanlanmış olur.

4. Yükleme işlemini tamamlamak için tüm örnek örneklerini Visual Studio.

## <a name="remove-the-extension"></a>Uzantıyı kaldırma

Uzantıyı Market'Visual Studio bilgisayarınızdan kaldırabilirsiniz.

### <a name="to-remove-the-extension-from-the-marketplace-via-command-line"></a>Uzantıyı marketten komut satırı aracılığıyla kaldırmak için

1. Uzantıyı kaldırmak için aşağıdaki komutu kullanın:

   ```
   VsixPublisher.exe deleteExtension -publisherName "TestVSIXPublisher" -extensionName "MyVsixExtension"
   ```

2. Uzantının başarıyla silinmesinin ardından aşağıdaki komut satırı iletisini alırsınız:

   ```
   Removed 'MyVsixExtension' from the Marketplace.
   ```

### <a name="to-remove-the-extension-from-your-computer"></a>Uzantıyı bilgisayarınızdan kaldırmak için

1. Bu Visual Studio Araçlar menüsünde **Uzantılar** ve **Güncelleştirmeler'e tıklayın**.

2. "MyVsixExtension" öğesini seçin ve kaldır'a **tıklayın**. Uzantı daha sonra kaldırılmak üzere zamanlanmış olur.

3. Kaldırma işlemini tamamlamak için tüm örnek örneklerini Visual Studio.
