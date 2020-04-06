---
title: Komut satırLarını kullanarak uzantıyayım
ms.date: 07/12/2018
ms.topic: conceptual
helpviewer_keywords:
- publishing extensions
- extension, publishing
ms.assetid: 6ff9efc4-919d-4071-a80d-6dbdd2ceb2f8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 40be0252218f39b4ff98b58caedd7f9f20ce6d5d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697122"
---
# <a name="walkthrough-publishing-a-visual-studio-extension-via-command-line"></a>Walkthrough: Komut satırı üzerinden Visual Studio uzantısı yayımlama

Bu izlik, komut satırını kullanarak Visual Studio Marketplace'te Visual Studio uzantısını nasıl yayınlayacağınızı gösterir. Uzantınızı Market'e eklediğinizde, geliştiriciler [**uzantılar ve güncelleştirmeler**](../ide/finding-and-using-visual-studio-extensions.md) iletişim kutusunu kullanarak yeni ve güncelleştirilmiş uzantılara göz atabilir.

VsixPublisher.exe, Visual Studio uzantılarını Pazar'a yayınlamak için komut satırı aracıdır. ${VSInstallDir}\VSSDK\VisualStudioIntegration\Tools\Bin\VsixPublisher.exe adresinden erişilebilir. Bu araçta bulunan komutlar şunlardır: **yayımlamak**, **createPublisher**, **deletePublisher**, **deleteExtension**, **login**, **logout**.

## <a name="commands"></a>Komutlar

### <a name="publish"></a>publish

Market'in uzantısıyayımdır. Uzantı bir vsix, exe/msi dosyası veya bir bağlantı olabilir. Uzantı zaten aynı sürümle varsa, uzantının üzerine yazar. Uzantı zaten yoksa, yeni bir uzantı oluşturur.

|Komut Seçenekleri |Açıklama |
|---------|---------|
|yük (gerekli) | Yayımlanmak için yüke giden bir yol veya "daha fazla bilgi URL'si" olarak kullanılacak bir bağlantı. |
|publishManifest (gerekli) | Yayımlanacak bildirim dosyasına giden yol. |
|yoksayUyarılar | Uzantı yayımlarken göz ardı edilen uyarıların listesi. Bu uyarılar, uzantı yayımlarken komut satırı iletileri olarak gösterilir. (örneğin, "VSIXValidatorWarning01, VSIXValidatorWarning02")
|personalAccessToken | Yayımcının kimliğini doğrulamak için kullanılan Kişisel Erişim Belirteci (PAT). Sağlanmazsa, PAT oturum açmış kullanıcılardan edinilir. |

```
VsixPublisher.exe publish -payload "{path to vsix}" -publishManifest "{path to vs-publish.json}" -ignoreWarnings "VSIXValidatorWarning01,VSIXValidatorWarning02"
```

### <a name="createpublisher"></a>createPublisher

Market'te bir yayımcı oluşturur. Ayrıca yayımcıyı gelecekteki eylemler için makineye kaydeder (örneğin, bir uzantıyı silme/yayımlama).

|Komut Seçenekleri |Açıklama |
|---------|---------|
|displayName (gerekli) | Yayımcının görüntü adı. |
|publisherName (gerekli) | Yayımcının adı (örneğin, tanımlayıcı). |
|personalAccessToken (gerekli) | Yayımcının kimliğini doğrulamak için kullanılan Kişisel Erişim Belirteci. |
|shortDescription | Yayımcının kısa bir açıklaması (dosya değil). |
|longDescription | Yayımcının uzun bir açıklaması (dosya değil). |

```
VsixPublisher.exe createPublisher -publisherName "{Publisher Name}" -displayName "{Publisher Display Name}" -personalAccessToken "{Personal Access Token}"
```

### <a name="deletepublisher"></a>deletePublisher

Market'teki bir yayımcıyı siler.

|Komut Seçenekleri |Açıklama |
|---------|---------|
|publisherName (gerekli) | Yayımcının adı (örneğin, tanımlayıcı). |
|personalAccessToken (gerekli) | Yayımcının kimliğini doğrulamak için kullanılan Kişisel Erişim Belirteci. |

```
VsixPublisher.exe deletePublisher -publisherName "{Publisher Name}" -personalAccessToken "{Personal Access Token}"
```

### <a name="deleteextension"></a>silmeUzatma

Market'ten bir uzantıyı siler.

|Komut Seçenekleri |Açıklama |
|---------|---------|
|extensionName (gerekli) | Silinecek uzantının adı. |
|publisherName (gerekli) | Yayımcının adı (örneğin, tanımlayıcı). |
|personalAccessToken | Yayımcının kimliğini doğrulamak için kullanılan Kişisel Erişim Belirteci. Sağlanmazsa, pat oturum açmış kullanıcılardan edinilir. |

```
VsixPublisher.exe deleteExtension -extensionName "{Extension Name}" -publisherName "{Publisher Name}"
```

### <a name="login"></a>oturum aç

Bir yayımcıyı makineye kaydeder.

|Komut Seçenekleri |Açıklama |
|---------|---------|
|personalAccessToken (gerekli | Yayımcının kimliğini doğrulamak için kullanılan Kişisel Erişim Belirteci. |
|publisherName (gerekli) | Yayımcının adı (örneğin, tanımlayıcı). |
|Üzerine | Varolan herhangi bir yayımcının yeni kişisel erişim belirteciyle birlikte üzerine yazılması gerektiğini belirtir. |

```
VsixPublisher.exe login -personalAccessToken "{Personal Access Token}" -publisherName "{Publisher Name}"
```

### <a name="logout"></a>logout

Bir yayımcıyı makineden çıkarır.

|Komut Seçenekleri |Açıklama |
|---------|---------|
|publisherName (gerekli) | Yayımcının adı (örneğin, tanımlayıcı). |
|yoksayEksikYayıncı | Belirtilen yayımcı zaten oturum açmış değilse aracın hata olmaması gerektiğini belirtir. |

```
VsixPublisher.exe logout -publisherName "{Publisher Name}"
```

## <a name="publishmanifest-file"></a>publishManifest dosyası

PublishManifest dosyası **yayımlama** komutu tarafından kullanılır. Marketin bilmesi gereken uzantıyla ilgili tüm meta verileri temsil eder. Yüklenen uzantı bir VSIX uzantısından geliyorsa, "kimlik" özelliği yalnızca "internalName" kümesine sahip olmalıdır. Bunun nedeni, "kimlik" özelliklerinin geri kalanının vsixmanifest dosyasından oluşturulabiliyor olmasıdır. Uzantı bir msi/exe veya bağlantı uzantısı ise, kullanıcı "kimlik" özelliğinde gerekli alanları sağlamalıdır. Bildirimin geri kalanı Pazar Alanına özgü bilgiler içerir (örneğin, kategoriler, Q&A etkin olup olmadığı, vb.

VSIX uzantısı yayımlamaManifest dosya örneği:

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

MSI/EXE veya LINK yayımlamaManifest dosya örneği:

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

Varlık dosyaları, okuma dosyasına görüntüler gibi şeyleri katıştırma için sağlanabilir. Örneğin, bir uzantıda aşağıdaki "genel bakış" Markdown belgesi varsa:

```markdown
TestExtension
...
This is test extension.
![Test logo](images/testlogo.png "Test logo")
```

Önceki örnekteki "images/testlogo.png"i çözmek için, bir kullanıcı yayımlama bildiriminde aşağıdaki gibi "assetFiles" sağlayabilir:

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

## <a name="publishing-walkthrough"></a>İznini yayımlama

### <a name="prerequisites"></a>Ön koşullar

Bu izlenmeyi takip etmek için Visual Studio SDK'yı yüklemeniz gerekir. Daha fazla bilgi için Visual [Studio SDK'yı yükleme ye](../extensibility/installing-the-visual-studio-sdk.md)bakın.

### <a name="create-a-visual-studio-extension"></a>Visual Studio uzantısı oluşturma

Bu durumda, varsayılan VSPackage uzantısı kullanacağız, ancak aynı adımlar her tür uzantı için geçerlidir.

1. C#'da menü komutu olan "TestPublish" adlı bir VSPackage oluşturun. Daha fazla bilgi için [Bkz. İlk Uzantıoluşturma: Hello World](../extensibility/extensibility-hello-world.md).

### <a name="package-your-extension"></a>Uzantınızı paketle

1. Ürün adı, yazar ve sürüm hakkında doğru bilgilerle uzantısı vsixmanifest'i güncelleştirin.

   ![uzantısı vsixmanifest güncelleme](media/update-extension-vsixmanifest.png)

2. Uzantınızı **Sürüm** modunda oluşturun. Şimdi uzantınız \bin\Release klasöründe VSIX olarak paketlenecektir.

3. Yüklemeyi doğrulamak için VSIX'yi çift tıklatabilirsiniz.

### <a name="test-the-extension"></a>Uzantıyı test edin

 Uzantıyı dağıtmadan önce, Visual Studio'nun deneysel örneğine doğru şekilde yüklendiğinden emin olmak için uzantıyı oluşturun ve test edin.

1. Visual Studio'da hata ayıklamaya başlayın. Visual Studio deneysel bir örnek açmak için.

2. Deneysel durumda, **Araçlar** menüsüne gidin ve **Uzantılar ve Güncellemeler'i tıklatın...**. TestPublish uzantısı orta bölmede görünmeli ve etkinleştirilmelidir.

3. **Araçlar** menüsünde test komutunu gördüğünüzden emin olun.

### <a name="publish-the-extension-to-the-marketplace-via-command-line"></a>Uzantıyı komut satırı üzerinden Market'e yayımlama

1. Uzantınızın Sürüm sürümünü oluşturduğundan ve güncel olduğundan emin olun.

2. Publishmanifest.json ve overview.md dosyaları oluşturduğunuzdan emin olun.

3. Komut satırLarını açın ve ${VSInstallDir}\VSSDK\VisualStudioIntegration\Tools\Bin\ dizinine gidin.

4. Yeni bir yayımcı oluşturmak için aşağıdaki komutu kullanın:

   ```
   VsixPublisher.exe createPublisher -publisherName "TestVSIXPublisher" -displayName "Test VSIX Publisher" -personalAccessToken "{Personal Access Token that is used to authenticate the publisher. If not provided, the pat is acquired from the logged-in users.}"
   ```

5. Yayımcının başarılı bir şekilde oluşturulmasında aşağıdaki komut satırı iletisini görürsünüz:

   ```
   Added 'Test VSIX Publisher' as a publisher on the Marketplace.
   ```

6. [Visual Studio Marketplace'e](https://marketplace.visualstudio.com/manage/publishers) göz atarak oluşturduğunuz yeni yayımcıyı doğrulayabilirsiniz

7. Yeni bir uzantı yayımlamak için aşağıdaki komutu kullanın:

   ```
   VsixPublisher.exe publish -payload "{Path to vsix file}"  -publishManifest "{path to publishManifest file}"
   ```

8. Yayımcının başarılı bir şekilde oluşturulmasında aşağıdaki komut satırı iletisini görürsünüz:

   ```
   Uploaded 'MyVsixExtension' to the Marketplace.
   ```

9. [Visual Studio Marketplace'e](https://marketplace.visualstudio.com/) yönlendirerek yayınladığınız yeni uzantıyı doğrulayabilirsiniz

### <a name="install-the-extension-from-the-visual-studio-marketplace"></a>Visual Studio Marketplace'ten uzantıyı yükleyin

Şimdi uzantısı yayımlanır, Visual Studio yükleyin ve orada test edin.

1. Visual Studio'da, **Araçlar** menüsünde **Uzantılar ve Güncellemeler'i tıklatın...**.

2. **Çevrimiçi'yi** tıklatın ve ardından TestPublish'i arayın.

3. **İndir'i**tıklatın. Uzantı daha sonra yüklemek için zamanlanır.

4. Yüklemeyi tamamlamak için Visual Studio'nun tüm örneklerini kapatın.

## <a name="remove-the-extension"></a>Uzantıyı kaldırma

Uzantıyı Visual Studio Marketplace'ten ve bilgisayarınızdan kaldırabilirsiniz.

### <a name="to-remove-the-extension-from-the-marketplace-via-command-line"></a>Komut satırı üzerinden uzantıyı Market'ten kaldırmak için

1. Bir uzantıyı kaldırmak istiyorsanız, aşağıdaki komutu kullanın:

   ```
   VsixPublisher.exe deleteExtension -publisherName "TestVSIXPublisher" -extensionName "MyVsixExtension"
   ```

2. Uzantının başarılı bir şekilde silinmesi üzerine aşağıdaki komut satırı iletisini görürsünüz:

   ```
   Removed 'MyVsixExtension' from the Marketplace.
   ```

### <a name="to-remove-the-extension-from-your-computer"></a>Uzantıyı bilgisayarınızdan kaldırmak için

1. Visual Studio'da, **Araçlar** menüsünde **Uzantılar ve Güncellemeler'i**tıklatın.

2. "MyVsixExtension" seçeneğini belirleyin ve **ardından Kaldır'ı**tıklatın. Uzantı daha sonra kaldırmak için zamanlanır.

3. Yüklemeyi tamamlamak için Visual Studio'nun tüm örneklerini kapatın.
