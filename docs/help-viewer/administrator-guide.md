---
title: Yardım Görüntüleyicisi Yönetici Kılavuzu
description: Microsoft Yardım Görüntüleyicisi Yönetici kılavuzunu okuyun. İnternet 'ten yerel yardım içeriği dağıtın veya istemci bilgisayarlarda önceden yüklenmiş yerel yardım içeriğini dağıtın.
ms.date: 11/01/2017
ms.topic: conceptual
ms.assetid: 4340c69f-b96b-4932-bb82-38b16a5ab149
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 312b886ee0becc794f657ecaaba7fb028d4b3cf1
ms.sourcegitcommit: dfbbf041e68ec3a4cd97196b19c9226a4793e702
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/09/2020
ms.locfileid: "91878897"
---
# <a name="help-viewer-administrator-guide"></a>Yardım Görüntüleyicisi Yönetici Kılavuzu

Yardım Görüntüleyicisi, internet erişimi olan veya olmayan ağ ortamları için yerel yardım yüklemelerini yönetmenizi sağlar. Yerel Yardım içeriği makineye göre yapılandırılır. Varsayılan olarak, kullanıcılar kendi yerel yardım yüklemelerini güncelleştirmek için yönetici haklarına sahip olmalıdır.

Ağ ortamınız istemcilerin internet 'e erişmesine izin veriyorsa, internet 'ten yerel yardım içeriği dağıtmak için **Yardım Içeriği Yöneticisi** yürütülebilirini kullanabilirsiniz. Komut satırı söz dizimi *HlpCtntMgr.exe* hakkında daha fazla bilgi için bkz. [Yardım Içerik Yöneticisi için komut satırı bağımsız değişkenleri](../help-viewer/command-line-arguments.md).

İçerik oluşturma, bir intranet hizmeti uç noktası ve benzer etkinlik türleri oluşturma hakkında bilgi için bkz. [Yardım GÖRÜNTÜLEYICISI SDK](../extensibility/internals/microsoft-help-viewer-sdk.md).

Ağ ortamınızda İnternet erişiminiz yoksa, Yardım Görüntüleyicisi intranet veya ağ paylaşımından yerel yardım içeriği dağıtabilir. Ayrıca, şu gibi işlevler için [kayıt defteri anahtarı geçersiz kılmalarını](../help-viewer/behavior-overrides.md) kullanarak VISUAL Studio IDE yardım seçeneklerini devre dışı bırakabilirsiniz:

- çevrimiçi ve çevrimdışı yardım

- IDE 'nin ilk başlatıldığında içerik yükleme

- intranet içerik hizmeti belirtme

- içeriği yönetme

## <a name="deploy-local-help-content-from-the-internet"></a>İnternet 'ten yerel yardım içeriği dağıtma

Internet 'ten istemci bilgisayarlara yerel yardım içeriği dağıtmak için **Yardım Içerik Yöneticisi** (*HlpCtntMgr.exe*) kullanabilirsiniz. Aşağıdaki sözdizimini kullanın:

```cmd
\\%ProgramFiles(x86)%\Microsoft Help Viewer\v2.3\HlpCtntmgr.exe /operation \<*name*> /catalogname \<*catalog name*> /locale \<*locale*>
```

Komut satırı söz dizimi *HlpCtntMgr.exe* hakkında daha fazla bilgi için bkz. [Yardım Içerik Yöneticisi için komut satırı bağımsız değişkenleri](../help-viewer/command-line-arguments.md).

Gereksinimler:

- İstemci bilgisayarların internet erişimi olmalıdır.

- Kullanıcılar yüklendikten sonra yerel yardım içeriğini güncelleştirmek, eklemek veya kaldırmak için yönetici haklarına sahip olmalıdır.

Uyarılar

- Yardım için varsayılan kaynak hala çevrimiçi olmaya devam edecektir.

### <a name="example"></a>Örnek

Aşağıdaki örnekte, Visual Studio için Ingilizce içerik bir istemci bilgisayara yüklenir.

#### <a name="to-install-english-content-from-the-internet"></a>Internet 'ten Ingilizce içerik yüklemek için

1. **Başlat** ' ı ve ardından **Çalıştır**' ı seçin.

2. Aşağıdakileri yazın:

     `C:\Program Files (x86)\Microsoft Help Viewer\v2.3\hlpctntmgr.exe /operation install /catalogname VisualStudio15 /locale en-us`

3.  **Enter** tuşuna basın.

## <a name="deploy-pre-installed-local-help-content-on-client-computers"></a>İstemci bilgisayarlarda önceden yüklenmiş yerel yardım içeriğini dağıtma

Çevrimiçi olarak bir bilgisayara bir içerik kümesi yükleyebilir ve sonra bu içerik kümesini diğer bilgisayarlara kopyalayabilirsiniz.

Gereksinimler:

- İçerik kümesini yüklediğiniz bilgisayar internet erişimine sahip olmalıdır.

- Kullanıcılar yüklendikten sonra yerel yardım içeriğini güncelleştirmek, eklemek veya kaldırmak için yönetici haklarına sahip olmalıdır.

    > [!TIP]
    > Kullanıcılar yönetici haklarına sahip değilse, yardım görüntüleyicisinde **Içeriği Yönet** sekmesini devre dışı bırakmanız önerilir. Daha fazla bilgi için bkz. [Yardım Içerik Yöneticisi geçersiz kılmaları](../help-viewer/behavior-overrides.md).

Uyarılar

- Yardım için varsayılan kaynak hala çevrimiçi olmaya devam edecektir.

### <a name="create-the-content-set"></a>İçerik kümesi oluşturma

Temel içerik kümesini oluşturabilmeniz için önce hedef bilgisayardaki tüm yerel Visual Studio içeriğini kaldırmanız gerekir.

#### <a name="to-uninstall-local-help"></a>Yerel yardım 'ı kaldırmak için

1. Yardım Görüntüleyicisi 'nde **Içeriği Yönet** sekmesini seçin.

2. Visual Studio belge kümesine gidin.

3. Her alt öğenin yanındaki **Kaldır** ' ı seçin.

4. Kaldırmak için **Güncelleştir** ' i seçin.

5. *%ProgramData%\Microsoft\HelpLibrary2\Catalogs\VisualStudio15* ' e gidin ve klasörün yalnızca dosya *catalogType.xml*içerdiğini doğrulayın.

   Daha önce yüklenmiş olan tüm yerel Visual Studio yardım içeriğini kaldırdıktan sonra, temel içerik kümesini indirmeye hazırlanın.

#### <a name="to-download-the-content"></a>İçeriği indirmek için

1. Yardım Görüntüleyicisi 'nde **Içeriği Yönet** sekmesini seçin.

2. **Önerilen belgeler** veya **kullanılabilir belgeler**altında, indirmek istediğiniz belge kümelerine gidin ve **Ekle**' yi seçin.

3. **Güncelleştir**' i seçin.

Daha sonra, içeriği istemci bilgisayarlara dağıtılabilmesi için paketlemeyi yapmanız gerekir.

#### <a name="to-package-the-content"></a>İçeriği paketlemek için

1. Daha sonra dağıtım için içeriği kopyalamak üzere bir klasör oluşturun. Örneğin: *C:\VSHelp*.

2. Yönetici izinleriyle *cmd.exe* açın.

3. Adım 1 ' de oluşturduğunuz klasöre gidin.

4. Aşağıdakileri yazın:

     `Xcopy %ProgramData%\Microsoft\HelpLibrary2 \<*foldername*>\ /y /e /k /o`

     Örnek: `Xcopy %ProgramData%\Microsoft\HelpLibrary2 c:\VSHelp\ /y /e /k /o`

### <a name="deploy-the-content"></a>İçeriği dağıtma

1. Bir ağ paylaşma oluşturun ve yardım içeriğini bu konuma kopyalayın.

     Örneğin, *C:\VSHelp* içindeki içeriği * \\ \myserver\VSHelp*'e kopyalayın.

2. Yardım içeriği için dağıtım betiğini içeren bir *. bat* dosyası oluşturun. İstemci, gönderim kapsamında silinmekte olan dosyaların hiçbirinde okuma kilidine sahip olduğundan, güncelleştirmeleri dağıtmadan önce istemcinin kapatılmasını sağlayabilirsiniz. Örneğin:

    ```cmd
    REM - copy pre-ripped content to ProgramData
    Xcopy %~dp0HelpLibrary2 %SYSTEMDRIVE%\ProgramData\Microsoft\HelpLibrary2\ /y /e /k /o
    if ERRORLEVEL 1 ECHO *** ERROR COPYING Help Library files to ProgramData (%ERRORLEVEL%)
    ```

3. Yardım içeriğini yüklemek istediğiniz yerel makinelerde *. bat* dosyasını çalıştırın.

## <a name="see-also"></a>Ayrıca bkz.

- [Yardım Içeriği Yöneticisi için komut satırı bağımsız değişkenleri](../help-viewer/command-line-arguments.md)
- [Yardım Içerik Yöneticisi geçersiz kılmaları](../help-viewer/behavior-overrides.md)
- [Microsoft Yardım Görüntüleyicisi](../help-viewer/overview.md)
- [Yardım Görüntüleyicisi SDK 'Sı](../extensibility/internals/microsoft-help-viewer-sdk.md)