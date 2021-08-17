---
title: Komut satırı kullanarak uzantı yayımlama
description: Geliştiricilerin yeni ve güncelleştirilmiş uzantılara göz atmalarına olanak sağlayan Visual Studio Market'te bir uzantı yayımlamak için komut satırı kullanmayı öğrenin.
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
ms.openlocfilehash: b6d02c4eb0125007086e209897e11b2038adc26d116cd0dd03f346fc02291a51
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121374604"
---
# <a name="walkthrough-publishing-a-visual-studio-extension-via-command-line"></a>Adım adım kılavuz: Komut Visual Studio uzantı yayımlama

Bu kılavuzda, komut satırı kullanarak Visual Studio markette Visual Studio uzantısını nasıl yayımlayabilirsiniz? Uzantınızı Market'e eklerken geliştiriciler Uzantılar ve Güncelleştirmeler iletişim [**kutusunu**](../ide/finding-and-using-visual-studio-extensions.md) kullanarak yeni ve güncelleştirilmiş uzantılara göz atabilir.

VsixPublisher.exe, Market'te Visual Studio yayımlamak için komut satırı aracıdır. ${VSInstallDir}veya ${VSInstallDir}\VSSDK\VisualStudioIntegration\Tools\Bin\VsixPublisher.exe. Bu araçta kullanılabilen komutlar: **yayımlama,** **createPublisher**, **deletePublisher**, **deleteExtension**, **login**, **logout**.

## <a name="commands"></a>Komutlar

### <a name="publish"></a>publish

Market'te bir uzantı yayımlar. Uzantı vsix, exe/msi dosyası veya bağlantı olabilir. Uzantı aynı sürümde zaten varsa, uzantının üzerine yazacak. Uzantı henüz yoksa, yeni bir uzantı oluşturacak.

|Komut Seçenekleri |Açıklama |
|---------|---------|
|yük (gerekli) | Yayımlayacak yükün yolu veya "daha fazla bilgi URL'si" olarak kullanmak üzere bir bağlantı. |
|publishManifest (gerekli) | Yayımla bildirim dosyasının yolu. |
|ignoreWarnings | Uzantı yayımlarken yoksaymak için uyarıların listesi. Bu uyarılar, bir uzantı yayımlarken komut satırı iletileri olarak gösterilir. (örneğin, "VSIXValidatorWarning01, VSIXValidatorWarning02")
|personalAccessToken | Yayımcının kimliğini doğrulamak için kullanılan Kişisel Erişim Belirteci (PAT). Sağlanmazsa, PAT oturum açmış kullanıcılardan edinilmiş olur. |

```
VsixPublisher.exe publish -payload "{path to vsix}" -publishManifest "{path to vs-publish.json}" -ignoreWarnings "VSIXValidatorWarning01,VSIXValidatorWarning02"
```

### <a name="createpublisher"></a>createPublisher

Market'te bir yayımcı oluşturur. Ayrıca, yayımcıyı gelecekteki eylemler (örneğin, uzantıyı silme/yayımlama) için makineye kaydeder.

|Komut Seçenekleri |Açıklama |
|---------|---------|
|displayName (gerekli) | Yayımcının görünen adı. |
|publisherName (gerekli) | Yayımcının adı (örneğin, tanımlayıcı). |
|personalAccessToken (gerekli) | Yayımcının kimliğini doğrulamak için kullanılan Kişisel Erişim Belirteci. |
|shortDescription | Yayımcının kısa açıklaması (dosya değil). |
|longDescription | Yayımcının uzun açıklaması (dosya değil). |

```
VsixPublisher.exe createPublisher -publisherName "{Publisher Name}" -displayName "{Publisher Display Name}" -personalAccessToken "{Personal Access Token}"
```

### <a name="deletepublisher"></a>deletePublisher

Market'te bir yayımcıyı siler.

|Komut Seçenekleri |Açıklama |
|---------|---------|
|publisherName (gerekli) | Yayımcının adı (örneğin, tanımlayıcı). |
|personalAccessToken (gerekli) | Yayımcının kimliğini doğrulamak için kullanılan Kişisel Erişim Belirteci. |

```
VsixPublisher.exe deletePublisher -publisherName "{Publisher Name}" -personalAccessToken "{Personal Access Token}"
```

### <a name="deleteextension"></a>deleteExtension

Market'te bir uzantıyı siler.

|Komut Seçenekleri |Açıklama |
|---------|---------|
|extensionName (gerekli) | Silinecek uzantının adı. |
|publisherName (gerekli) | Yayımcının adı (örneğin, tanımlayıcı). |
|personalAccessToken | Yayımcının kimliğini doğrulamak için kullanılan Kişisel Erişim Belirteci. Sağlanmazsa, pat oturum açmış kullanıcılardan edinilmiş olur. |

```
VsixPublisher.exe deleteExtension -extensionName "{Extension Name}" -publisherName "{Publisher Name}"
```

### <a name="login"></a>oturum aç

Makineye bir yayımcı kaydeder.

|Komut Seçenekleri |Açıklama |
|---------|---------|
|personalAccessToken (gerekli) | Yayımcının kimliğini doğrulamak için kullanılan Kişisel Erişim Belirteci. |
|publisherName (gerekli) | Yayımcının adı (örneğin, tanımlayıcı). |
|Üzerine | Mevcut yayımcıların üzerine yeni kişisel erişim belirteci yazılması gerektiğini belirtir. |

```
VsixPublisher.exe login -personalAccessToken "{Personal Access Token}" -publisherName "{Publisher Name}"
```

### <a name="logout"></a>logout

Bir yayımcıyı makineden günlüğe kaydeder.

|Komut Seçenekleri |Açıklama |
|---------|---------|
|publisherName (gerekli) | Yayımcının adı (örneğin, tanımlayıcı). |
|ignoreMissingPublisher | Belirtilen yayımcı zaten oturum açmamışsa aracın hataya neden olması gerektiğini belirtir. |

```
VsixPublisher.exe logout -publisherName "{Publisher Name}"
```

## <a name="publishmanifest-file"></a>publishManifest dosyası

publishManifest dosyası publish komutu **tarafından** kullanılır. Market'in bilmek zorunda olduğu uzantıyla ilgili tüm meta verileri temsil eder. Karşıya yüklenen uzantı bir VSIX uzantısındansa, "identity" özelliği yalnızca "internalName" ayarlanmıştır. Bunun nedeni, "kimlik" özelliklerinin geri kalanının vsixmanifest dosyasından oluşturula çalışmasıdır. Uzantı bir msi/exe veya bağlantı uzantısı ise, kullanıcının "kimlik" özelliğinde gerekli alanları sağlaması gerekir. Bildirimin geri kalanında Market'e özgü bilgiler (örneğin kategoriler, Soru-Cevap'ın etkin olup&vb.) bulunur.

VSIX uzantısı publishManifest dosya örneği:

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

MSI/EXE veya LINK publishManifest dosya örneği:

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

Varlık dosyaları, beni okundu dosyasına görüntüler gibi şeyler eklemek için sağlanmıştır. Örneğin, bir uzantı aşağıdaki "genel bakış" Markdown belgesine sahipse:

```markdown
TestExtension
...
This is test extension.
![Test logo](images/testlogo.png "Test logo")
```

Bir kullanıcı, önceki örnekte yer alan "images/testlogo.png" sorununu çözmek için aşağıdaki gibi yayımlama bildiriminde "assetFiles" sağlanmıştır:

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

## <a name="publishing-walkthrough"></a>Yayımlama yönergesi

### <a name="prerequisites"></a>Önkoşullar

Bu izlenecek yolu takip etmek için Visual Studio SDK'sı yüklemeniz gerekir. Daha fazla bilgi için [bkz. Visual Studio SDK'sı yükleme.](../extensibility/installing-the-visual-studio-sdk.md)

### <a name="create-a-visual-studio-extension"></a>Bir Visual Studio oluşturma

Bu durumda varsayılan VSPackage uzantısını kullanacağız ancak aynı adımlar her uzantı için geçerlidir.

1. C# içinde menü komutu olan "TestPublish" adlı bir VSPackage oluşturun. Daha fazla bilgi için [bkz. İlk Uzantınızı Oluşturma: Merhaba Dünya.](../extensibility/extensibility-hello-world.md)

### <a name="package-your-extension"></a>Uzantınızı paketle

1. vsixmanifest uzantısını ürün adı, yazarı ve sürümü hakkında doğru bilgilerle güncelleştirin.

   ![uzantı vsixmanifest'i güncelleştirme](media/update-extension-vsixmanifest.png)

2. Uzantınızı Yayın **modunda** derleme. Artık uzantınız \bin\Release klasöründe VSIX olarak paketlensin.

3. VsIX'e çift tıklar ve yükleme işlemini doğrularsınız.

### <a name="test-the-extension"></a>Uzantıyı test etmek

 Uzantıyı dağıtmadan önce, deneysel Visual Studio'nin deneysel örneğinde doğru şekilde yüklü olduğundan emin olmak için uzantıyı Visual Studio.

1. Bu Visual Studio hata ayıklamayı başlat. deneme örneği açmak için Visual Studio.

2. Deneysel örnekte Araçlar menüsüne gidin ve **Uzantılar** ve **Güncelleştirmeler... seçeneğine tıklayın.** TestPublish uzantısı orta bölmede görün olmalı ve etkinleştirilmelidir.

3. Araçlar **menüsünde** test komutunu gördüğünüzden emin olun.

### <a name="publish-the-extension-to-the-marketplace-via-command-line"></a>Uzantıyı komut satırı aracılığıyla Market'te yayımlama

1. Uzantının Yayın sürümünü ve güncel olduğundan emin olun.

2. Dosyaları üzerinde ve publishmanifest.jsoluşturduğunuzdan overview.md olun.

3. Komut satırı açın ve ${VSInstallDir}\VSSDK\VisualStudioIntegration\Tools\Bin\ dizinine gidin.

4. Yeni bir yayımcı oluşturmak için aşağıdaki komutu kullanın:

   ```
   VsixPublisher.exe createPublisher -publisherName "TestVSIXPublisher" -displayName "Test VSIX Publisher" -personalAccessToken "{Personal Access Token that is used to authenticate the publisher. If not provided, the pat is acquired from the logged-in users.}"
   ```

5. Yayımcının başarıyla oluşturulmasında aşağıdaki komut satırı iletisini alırsınız:

   ```
   Added 'Test VSIX Publisher' as a publisher on the Marketplace.
   ```

6. Oluşturduğunuz yeni yayımcıyı Market'e giderek Visual Studio [doğruabilirsiniz](https://marketplace.visualstudio.com/manage/publishers)

7. Yeni bir uzantı yayımlamak için aşağıdaki komutu kullanın:

   ```
   VsixPublisher.exe publish -payload "{Path to vsix file}"  -publishManifest "{path to publishManifest file}"
   ```

8. Yayımcının başarıyla oluşturulmasında aşağıdaki komut satırı iletisini alırsınız:

   ```
   Uploaded 'MyVsixExtension' to the Marketplace.
   ```

9. Visual Studio Market'e giderek yayımladığınız [yeni uzantıyı doğruabilirsiniz](https://marketplace.visualstudio.com/)

### <a name="install-the-extension-from-the-visual-studio-marketplace"></a>Visual Studio Market'Visual Studio yükleme

Artık uzantı yayımlanır ve uzantıyı Visual Studio ve orada test sınayın.

1. Bu Visual Studio Araçlar menüsünde **Uzantılar** ve **Güncelleştirmeler... seçeneğine tıklayın.**

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

1. Bu Visual Studio Araçlar menüsünde **Uzantılar** ve **Güncelleştirmeler'e tıklayın.**

2. "MyVsixExtension" öğesini seçin ve **kaldır'a tıklayın.** Uzantı daha sonra kaldırılmak üzere zamanlanmış olur.

3. Kaldırma işlemini tamamlamak için tüm örnek örneklerini Visual Studio.
