---
title: Uzantı komut satırını kullanarak Yayımla
description: Visual Studio Market bir uzantıyı kullanarak, geliştiricilerin yeni ve güncelleştirilmiş uzantılara gözatmasına olanak tanıyan bir uzantı yayımlamak için komut satırını nasıl kullanacağınızı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 07/12/2018
ms.topic: how-to
helpviewer_keywords:
- publishing extensions
- extension, publishing
ms.assetid: 6ff9efc4-919d-4071-a80d-6dbdd2ceb2f8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c4132d878ff1ec7689be890446a1849577fafd30
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/05/2021
ms.locfileid: "97877929"
---
# <a name="walkthrough-publishing-a-visual-studio-extension-via-command-line"></a>İzlenecek yol: komut satırı aracılığıyla Visual Studio uzantısı yayımlama

Bu izlenecek yol, komut satırını kullanarak Visual Studio Market Visual Studio uzantısını nasıl yayımlayacağınızı gösterir. Uzantınızı Market 'e eklediğinizde, geliştiriciler [**uzantıları ve güncelleştirmeler**](../ide/finding-and-using-visual-studio-extensions.md) iletişim kutusunu kullanarak yeni ve güncelleştirilmiş uzantılara gözatabilirler.

VsixPublisher.exe, Market 'e Visual Studio uzantıları yayımlamaya yönelik komut satırı aracıdır. $ {VSInstallDir} \VSSDK\VisualStudioIntegration\Tools\Bin\VsixPublisher.exe adresinden erişilebilir. Bu araçta kullanılabilen komutlar şunlardır: **Publish**, **CreatePublisher**, **deletepublisher**, **deleteextension**, **login**, **Logout**.

## <a name="commands"></a>Komutlar

### <a name="publish"></a>publish

Market 'e bir uzantı yayımlar. Uzantı bir VSIX, bir exe/MSI dosyası ya da bir bağlantı olabilir. Aynı sürüme sahip uzantı zaten varsa, uzantının üzerine yazar. Uzantı yoksa, yeni bir uzantı oluşturacaktır.

|Komut seçenekleri |Açıklama |
|---------|---------|
|Yük (gerekli) | Yayımlanacak yükün yolu veya "daha fazla bilgi URL 'SI" olarak kullanılacak bir bağlantı. |
|publishManifest (gerekli) | Kullanılacak yayımlama bildirimi dosyasının yolu. |
|ıgnoreuyarılarla | Uzantı yayımlanırken yoksayılacak uyarıların listesi. Bu uyarılar, bir uzantı yayımlarken komut satırı iletileri olarak gösterilir. (örneğin, "VSIXValidatorWarning01, VSIXValidatorWarning02")
|personalAccessToken | Yayımcının kimliğini doğrulamak için kullanılan kişisel erişim belirteci (PAT). Sağlanmazsa, PAT oturum açmış kullanıcılardan elde edilir. |

```
VsixPublisher.exe publish -payload "{path to vsix}" -publishManifest "{path to vs-publish.json}" -ignoreWarnings "VSIXValidatorWarning01,VSIXValidatorWarning02"
```

### <a name="createpublisher"></a>createPublisher

Market 'te bir Yayımcı oluşturur. Ayrıca, gelecekteki eylemler için yayımcıyı makineye de kaydeder (örneğin, bir uzantıyı silme/yayımlama).

|Komut seçenekleri |Açıklama |
|---------|---------|
|displayName (gerekli) | Yayımcının görünen adı. |
|publisherName (gerekli) | Yayımcının adı (örneğin, tanımlayıcı). |
|personalAccessToken (gerekli) | Yayımcının kimliğini doğrulamak için kullanılan kişisel erişim belirteci. |
|shortDescription | Yayımcının kısa bir açıklaması (dosya değil). |
|longDescription | Yayımcının uzun açıklaması (dosya değil). |

```
VsixPublisher.exe createPublisher -publisherName "{Publisher Name}" -displayName "{Publisher Display Name}" -personalAccessToken "{Personal Access Token}"
```

### <a name="deletepublisher"></a>deletePublisher

Market 'teki bir yayımcıyı siler.

|Komut seçenekleri |Açıklama |
|---------|---------|
|publisherName (gerekli) | Yayımcının adı (örneğin, tanımlayıcı). |
|personalAccessToken (gerekli) | Yayımcının kimliğini doğrulamak için kullanılan kişisel erişim belirteci. |

```
VsixPublisher.exe deletePublisher -publisherName "{Publisher Name}" -personalAccessToken "{Personal Access Token}"
```

### <a name="deleteextension"></a>deleteExtension

Marketten bir uzantıyı siler.

|Komut seçenekleri |Açıklama |
|---------|---------|
|extensionName (gerekli) | Silinecek uzantının adı. |
|publisherName (gerekli) | Yayımcının adı (örneğin, tanımlayıcı). |
|personalAccessToken | Yayımcının kimliğini doğrulamak için kullanılan kişisel erişim belirteci. Sağlanmazsa, Pat oturum açmış kullanıcılardan elde edilir. |

```
VsixPublisher.exe deleteExtension -extensionName "{Extension Name}" -publisherName "{Publisher Name}"
```

### <a name="login"></a>oturum aç

Bir yayımcıyı makineye kaydeder.

|Komut seçenekleri |Açıklama |
|---------|---------|
|personalAccessToken (gerekli | Yayımcının kimliğini doğrulamak için kullanılan kişisel erişim belirteci. |
|publisherName (gerekli) | Yayımcının adı (örneğin, tanımlayıcı). |
|yazılacak | Mevcut bir yayımcının yeni kişisel erişim belirteci ile üzerine yazılması gerektiğini belirtir. |

```
VsixPublisher.exe login -personalAccessToken "{Personal Access Token}" -publisherName "{Publisher Name}"
```

### <a name="logout"></a>logout

Makinenin bir yayımcısını günlüğe kaydeder.

|Komut seçenekleri |Açıklama |
|---------|---------|
|publisherName (gerekli) | Yayımcının adı (örneğin, tanımlayıcı). |
|ıgnoremissingpublisher | Belirtilen yayımcı zaten oturum açmadıysa aracın hata olmaması gerektiğini belirtir. |

```
VsixPublisher.exe logout -publisherName "{Publisher Name}"
```

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

### <a name="prerequisites"></a>Ön koşullar

Bu yönergeyi izlemek için, Visual Studio SDK 'sını yüklemelisiniz. Daha fazla bilgi için bkz. [Visual Studio SDK 'Yı yükleme](../extensibility/installing-the-visual-studio-sdk.md).

### <a name="create-a-visual-studio-extension"></a>Visual Studio uzantısı oluşturma

Bu durumda, varsayılan VSPackage uzantısını kullanacağız, ancak her uzantı türü için aynı adımlar geçerlidir.

1. Bir menü komutuna sahip "TestPublish" adlı C# dilinde VSPackage oluşturun. Daha fazla bilgi için, bkz. [Ilk uzantınızı oluşturma: Merhaba Dünya](../extensibility/extensibility-hello-world.md).

### <a name="package-your-extension"></a>Uzantınızı paketleyin

1. Valtmanifest uzantısını ürün adı, yazarı ve sürümü hakkındaki doğru bilgilerle güncelleştirin.

   ![Uzantı valtbildirimini Güncelleştir](media/update-extension-vsixmanifest.png)

2. Uzantınızı **yayın** modunda derleyin. Şimdi uzantınızın, \bin\Release klasöründe bir VSıX olarak paketlenmesi gerekir.

3. Yüklemeyi doğrulamak için VSıX 'e çift tıklayabilirsiniz.

### <a name="test-the-extension"></a>Uzantıyı test etme

 Uzantıyı dağıtmadan önce, Visual Studio 'nun deneysel örneğine doğru yüklendiğinden emin olmak için oluşturun ve test edin.

1. Visual Studio 'da hata ayıklamayı başlatın. Visual Studio 'nun deneysel bir örneğini açmak için.

2. Deneysel örnekte, **Araçlar** menüsüne gidin ve **Uzantılar ve güncelleştirmeler...** öğesine tıklayın. TestPublish uzantısı Orta bölmede görünmelidir ve etkinleştirilmelidir.

3. **Araçlar** menüsünde, test komutunu görtığınızdan emin olun.

### <a name="publish-the-extension-to-the-marketplace-via-command-line"></a>Uzantıyı komut satırı aracılığıyla Market 'e yayımlayın

1. Uzantınızın yayın sürümünü derlediğinizden ve güncel olduğundan emin olun.

2. Üzerinde publishmanifest.jsve overview.md dosyaları oluşturmuş olduğunuzdan emin olun.

3. Komut satırını açın ve $ {VSInstallDir} \VSSDK\VisualStudioIntegration\Tools\Bin\ dizinine gidin.

4. Yeni bir yayımcı oluşturmak için aşağıdaki komutu kullanın:

   ```
   VsixPublisher.exe createPublisher -publisherName "TestVSIXPublisher" -displayName "Test VSIX Publisher" -personalAccessToken "{Personal Access Token that is used to authenticate the publisher. If not provided, the pat is acquired from the logged-in users.}"
   ```

5. Yayımcının başarıyla oluşturulması sırasında aşağıdaki komut satırı iletisini görürsünüz:

   ```
   Added 'Test VSIX Publisher' as a publisher on the Marketplace.
   ```

6. [Visual Studio Market](https://marketplace.visualstudio.com/manage/publishers) giderek oluşturduğunuz yeni yayımcıyı doğrulayabilirsiniz.

7. Yeni bir uzantı yayımlamak için aşağıdaki komutu kullanın:

   ```
   VsixPublisher.exe publish -payload "{Path to vsix file}"  -publishManifest "{path to publishManifest file}"
   ```

8. Yayımcının başarıyla oluşturulması sırasında aşağıdaki komut satırı iletisini görürsünüz:

   ```
   Uploaded 'MyVsixExtension' to the Marketplace.
   ```

9. [Visual Studio Market](https://marketplace.visualstudio.com/) giderek yayımladığınız yeni uzantıyı doğrulayabilirsiniz

### <a name="install-the-extension-from-the-visual-studio-marketplace"></a>Uzantıyı Visual Studio Market yüklediğinizde

Artık uzantı yayımlandığına göre, Visual Studio 'Ya yükleyip test edin.

1. Visual Studio 'da, **Araçlar** menüsünde **Uzantılar ve güncelleştirmeler**' e tıklayın...

2. **Çevrimiçi** ' e tıklayın ve ardından TestPublish için arama yapın.

3. **İndir**’e tıklayın. Uzantı daha sonra yüklenmek üzere zamanlanır.

4. Yüklemeyi gerçekleştirmek için Visual Studio 'nun tüm örneklerini kapatın.

## <a name="remove-the-extension"></a>Uzantıyı kaldırma

Uzantıyı Visual Studio Market ve bilgisayarınızdan kaldırabilirsiniz.

### <a name="to-remove-the-extension-from-the-marketplace-via-command-line"></a>Uzantıyı Market 'ten komut satırı aracılığıyla kaldırma

1. Bir uzantıyı kaldırmak istiyorsanız aşağıdaki komutu kullanın:

   ```
   VsixPublisher.exe deleteExtension -publisherName "TestVSIXPublisher" -extensionName "MyVsixExtension"
   ```

2. Uzantının başarıyla silinmesinin ardından aşağıdaki komut satırı iletisini görürsünüz:

   ```
   Removed 'MyVsixExtension' from the Marketplace.
   ```

### <a name="to-remove-the-extension-from-your-computer"></a>Uzantıyı bilgisayarınızdan kaldırmak için

1. Visual Studio 'da, **Araçlar** menüsünde **Uzantılar ve güncelleştirmeler**' e tıklayın.

2. "Myvaltextension" öğesini seçin ve ardından **Kaldır**' a tıklayın. Daha sonra uzantı kaldırma işlemi için zamanlanır.

3. Kaldırma işlemini gerçekleştirmek için Visual Studio 'nun tüm örneklerini kapatın.
