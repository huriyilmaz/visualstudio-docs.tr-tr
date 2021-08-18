---
title: Yardım Görüntüleyicisi yönetici kılavuzu
description: Yönetici Microsoft Yardım Görüntüleyicisi okuyun. İnternet'den yerel Yardım içeriği dağıtın veya istemci bilgisayarlara önceden yüklenmiş yerel Yardım içeriğini dağıtın.
ms.date: 11/01/2017
ms.topic: conceptual
ms.assetid: 4340c69f-b96b-4932-bb82-38b16a5ab149
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-help-viewer
ms.workload:
- multiple
ms.openlocfilehash: f7f7256c806c0e7198569c2d323895d74f78ee03
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122151996"
---
# <a name="help-viewer-administrator-guide"></a>Yardım Görüntüleyicisi yönetici kılavuzu

Yardım Görüntüleyicisi, İnternet erişimi olan veya olmayan ağ ortamları için yerel Yardım yüklemelerini yönetmenize olanak tanır. Yerel yardım içeriği makine başına temelinde yapılandırılır. Varsayılan olarak, kullanıcıların yerel Yardım yüklemelerini güncelleştirmek için yönetici haklarına sahip olması gerekir.

Ağ ortamınız istemcilerin internete erişmesini sağlarsa, yerel Yardım içeriğini internetten dağıtmak için **Yardım İçerik** Yöneticisi yürütülebilir dosyasını kullanabilirsiniz. Komut satırı söz *dizimHlpCtntMgr.exe* daha fazla bilgi için bkz. [Yardım İçerik Yöneticisi için komut satırı bağımsız değişkenleri.](../help-viewer/command-line-arguments.md)

İçerik oluşturma, intranet hizmet uç noktası oluşturma ve benzer etkinlik türleri hakkında bilgi için bkz. Yardım Görüntüleyici [SDK'sı.](../extensibility/internals/microsoft-help-viewer-sdk.md)

Ağ ortamınıza İnternet erişiminiz yoksa, Yardım Görüntüleyici intranetten veya bir ağ paylaşımından yerel Yardım içeriğini dağıtabilirsiniz. Ayrıca, aşağıdaki Visual Studio kayıt defteri anahtarı geçersiz kılmalarını kullanarak IDE Yardım [seçeneklerini](../help-viewer/behavior-overrides.md) devre dışı abilirsiniz:

- çevrimiçi ve çevrimdışı yardım karşılaştırması

- IDE'nin ilk başlatılmasında içerik yüklemesi

- intranet içerik hizmeti belirtme

- içeriği yönetme

## <a name="deploy-local-help-content-from-the-internet"></a>İnternet'den yerel Yardım içeriği dağıtma

İnternetten istemci **bilgisayarlara yerel** *YardımHlpCtntMgr.exe* dağıtmak için Yardım İçerik Yöneticisi'ni (HlpCtntMgr.exe) kullanabilirsiniz. Aşağıdaki söz dizimlerini kullanın:

```cmd
\\%ProgramFiles(x86)%\Microsoft Help Viewer\v2.3\HlpCtntmgr.exe /operation \<*name*> /catalogname \<*catalog name*> /locale \<*locale*>
```

Komut satırı söz *dizimHlpCtntMgr.exe* daha fazla bilgi için bkz. [Yardım İçerik Yöneticisi için komut satırı bağımsız değişkenleri.](../help-viewer/command-line-arguments.md)

Gereksinimler:

- İstemci bilgisayarların İnternet erişimine sahip olması gerekir.

- Kullanıcıların, yüklendikten sonra yerel Yardım içeriğini güncelleştirmek, eklemek veya kaldırmak için yönetici haklarına sahip olması gerekir.

Uyarılar:

- Yardım için varsayılan kaynak hala çevrimiçi olacaktır.

### <a name="example"></a>Örnek

Aşağıdaki örnekte, istemci bilgisayara Visual Studio İngilizce içerik yüklenir.

#### <a name="to-install-english-content-from-the-internet"></a>İnternet'den İngilizce içerik yüklemek için

1. **Başlat'ı** ve ardından Çalıştır'ı **seçin.**

2. Aşağıdakileri yazın:

     `C:\Program Files (x86)\Microsoft Help Viewer\v2.3\hlpctntmgr.exe /operation install /catalogname VisualStudio15 /locale en-us`

3.  **Enter** tuşuna basın.

## <a name="deploy-pre-installed-local-help-content-on-client-computers"></a>İstemci bilgisayarlara önceden yüklenmiş yerel Yardım içeriğini dağıtma

Çevrimiçi bir içerik kümesinden bir bilgisayara yükleyebilir ve ardından yüklü olan içerik kümelerini diğer bilgisayarlara kopyaabilirsiniz.

Gereksinimler:

- İçerik kümesi yüklemek için bilgisayar İnternet erişimine sahip olmalıdır.

- Kullanıcıların, yüklendikten sonra yerel Yardım içeriğini güncelleştirmek, eklemek veya kaldırmak için yönetici haklarına sahip olması gerekir.

    > [!TIP]
    > Kullanıcıların yönetici hakları yoksa, Yardım Görüntüleyicisi'nde İçeriği Yönet **sekmesini** devre dışı bırakmanız önerilir. Daha fazla bilgi için [bkz. Help Content Manager geçersiz kılmaları.](../help-viewer/behavior-overrides.md)

Uyarılar:

- Yardım için varsayılan kaynak hala çevrimiçi olacaktır.

### <a name="create-the-content-set"></a>İçerik kümesi oluşturma

Temel içerik kümesi oluşturamadan önce hedef bilgisayarda tüm yerel Visual Studio içeriğini kaldırmanız gerekir.

#### <a name="to-uninstall-local-help"></a>Yerel yardımı kaldırmak için

1. Yardım Görüntüleyicisi'nde İçeriği Yönet **sekmesini** seçin.

2. Visual Studio kümesine gidin.

3. Her **alt öğenin** yanındaki Kaldır'ı seçin.

4. Kaldırmak için **Güncelleştir'i** seçin.

5. *%ProgramData%\Microsoft\HelpLibrary2\Catalogs\VisualStudio15* dizinine göz atarak klasörün yalnızca dosya *catalogType.xml.*

   Daha önce yüklenmiş olan tüm yerel Visual Studio yardım içeriğini kaldırmış olduktan sonra, temel içerik kümesi indirmeye hazır oluruz.

#### <a name="to-download-the-content"></a>İçeriği indirmek için

1. Yardım Görüntüleyicisi'nde İçeriği Yönet **sekmesini** seçin.

2. Önerilen **Belgeler veya Kullanılabilir** Belgeler **altında,** indirmek istediğiniz belge kümelerini gidin ve Ekle'yi **seçin.**

3. **Güncelleştir'i seçin.**

Ardından, içeriği istemci bilgisayarlara dağıtılacak şekilde paketleyebilirsiniz.

#### <a name="to-package-the-content"></a>İçeriği pakete dahil etmek için

1. İçeriği daha sonra dağıtım için klasörüne kopyalamak için bir klasör oluşturun. Örneğin: *C:\VSHelp*.

2. Yönetici *cmd.exe* ile oturum açın.

3. 1. adımda oluşturduğunuz klasöre gidin.

4. Aşağıdakileri yazın:

     `Xcopy %ProgramData%\Microsoft\HelpLibrary2 \<*foldername*>\ /y /e /k /o`

     Örnek: `Xcopy %ProgramData%\Microsoft\HelpLibrary2 c:\VSHelp\ /y /e /k /o`

### <a name="deploy-the-content"></a>İçeriği dağıtma

1. Bir ağ paylaşımı oluşturun ve yardım içeriğini bu konuma kopyalayın.

     Örneğin, *C:\VSHelp'te içeriği* *\\ \myserver\VSHelp klasörüne kopyalayın.*

2. Yardım *.bat* dağıtım betiği içeren bir dosya oluşturun. İstemci, anında yüklemenin bir parçası olarak silinen dosyaların herhangi biri üzerinde okuma kilidine sahip olabilir çünkü güncelleştirmeleri yüklemeden önce istemcinin kapanması gerekir. Örnek:

    ```cmd
    REM - copy pre-ripped content to ProgramData
    Xcopy %~dp0HelpLibrary2 %SYSTEMDRIVE%\ProgramData\Microsoft\HelpLibrary2\ /y /e /k /o
    if ERRORLEVEL 1 ECHO *** ERROR COPYING Help Library files to ProgramData (%ERRORLEVEL%)
    ```

3. Yardım *.bat* yüklemek istediğiniz yerel makinelerde uygulama dosyasını çalıştırın.

## <a name="see-also"></a>Ayrıca bkz.

- [Yardım İçerik Yöneticisi için komut satırı bağımsız değişkenleri](../help-viewer/command-line-arguments.md)
- [Help Content Manager geçersiz kılmaları](../help-viewer/behavior-overrides.md)
- [Microsoft Yardım Görüntüleyicisi](../help-viewer/overview.md)
- [Yardım Görüntüleyici SDK'sı](../extensibility/internals/microsoft-help-viewer-sdk.md)