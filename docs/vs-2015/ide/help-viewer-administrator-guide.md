---
title: Yardım Görüntüleyicisi Yönetici Kılavuzu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-help-viewer
ms.topic: conceptual
ms.assetid: 4340c69f-b96b-4932-bb82-38b16a5ab149
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 03cacd8de574de92002b44b237cd84c22e761eaf
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72645571"
---
# <a name="help-viewer-administrator-guide"></a>Yardım Görüntüleyicisi Yönetici Kılavuzu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Yardım Görüntüleyicisi, internet erişimi olan veya olmayan ağ ortamları için yerel yardım yüklemelerini yönetmenizi sağlar. Yerel Yardım içeriği makineye göre yapılandırılır. Varsayılan olarak, kullanıcılar kendi yerel yardım yüklemelerini güncelleştirmek için yönetici haklarına sahip olmalıdır.

 Ağ ortamınız istemcilerin internet 'e erişmesine izin veriyorsa, Yardım Görüntüleyicisi, yerel yardım içeriğini Internet 'ten dağıtmak için komut satırı betikleri kullanmanıza olanak sağlar.

 Ağ ortamınız istemcilerin internet 'e erişmesine izin vermediğinden, Yardım Görüntüleyicisi intranet veya ağ paylaşımından yerel yardım içeriği dağıtabilir. Çevrimiçi/çevrimdışı yardım, IDE 'nin ilk başlangıcında içerik yükleme, intranet içerik hizmeti belirtme ve kayıt defteri anahtarı geçersiz kılmalarını kullanarak içerik yönetme gibi Visual Studio IDE yardımı seçeneklerini de devre dışı bırakabilirsiniz.

 Temel sözdizimi aşağıdaki gibidir:

 > \HlpCtntmgr.exe/Operation \<*bağımsız değişkeninin*\<*yolu*>/katalogadı \<*Name*>/locale \<*locale*>/SourceUri \< *. msha yolu veya URL* 0

 HlpCtntMgr. exe komut satırı sözdizimi hakkında daha fazla bilgi için bkz. [Yardım Içeriği Yöneticisi Için komut satırı bağımsız değişkenleri](../ide/command-line-arguments-for-the-help-content-manager.md).

 İçerik oluşturma, intranet hizmeti uç noktası oluşturma ve benzer etkinlik türleri hakkında daha fazla bilgi için bkz. Yardım Görüntüleyicisi SDK.

## <a name="deploying-local-help-content-from-the-internet"></a>Internet 'ten yerel yardım Içeriği dağıtma
 Internet 'ten istemci bilgisayarlara yerel yardım içeriği dağıtmak için MSDN Içerik paketi hizmetini kullanabilirsiniz. Aşağıdaki sözdizimini kullanın:

 > \V2,2\HlpCtntmgr.exe/Operation \<*ad*>/katalogadı \<*Katalog adı*>/locale \<*locale* > \\ <*yolu*

 HlpCtntMgr. exe komut satırı sözdizimi hakkında daha fazla bilgi için bkz. [Yardım Içeriği Yöneticisi Için komut satırı bağımsız değişkenleri](../ide/command-line-arguments-for-the-help-content-manager.md).

 Gereklilik

- İstemci bilgisayarların Internet erişimi olmalıdır.

- Kullanıcılar yüklendikten sonra yerel yardım içeriğini güncelleştirmek, eklemek veya kaldırmak için yönetici haklarına sahip olmalıdır.

  Uyarılar

- Yardım için varsayılan kaynak hala çevrimiçi olmaya devam edecektir.

  > [!TIP]
  > Yardım için varsayılan kaynağı, HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\14.0\help\UseOnlineHelp kayıt defteri anahtarını değiştirerek değiştirebilirsiniz. Daha fazla bilgi için bkz. [Yardım Içerik Yöneticisi geçersiz kılmaları](../ide/help-content-manager-overrides.md).

- İstemcilere, Visual Studio 'nun ilk başlatıldığında temel yardım içeriğini yüklemeleri istenir. HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\VisualStudio\14.0\Help\DisableFirstRunHelpSelection kayıt defteri anahtarını değiştirerek bu istemi devre dışı bırakabilirsiniz.

### <a name="example"></a>Örnek
 Aşağıdaki örnekte, Visual Studio için Ingilizce içerik bir istemci bilgisayara yüklenir.

##### <a name="to-install-english-content-from-the-internet"></a>Internet 'ten Ingilizce içerik yüklemek için

1. **Başlat** ' ı ve ardından **Çalıştır**' ı seçin.

2. Aşağıdakileri yazın:

     C:\Program Files (x86) \Microsoft Help Viewer\v2,2\HlpCtntmgr.exe/Operation install/katalogadı VisualStudio14/locale en-US

3. ENTER tuşuna basın.

## <a name="deploying-pre-installed-local-help-content-on-client-computers"></a>Istemci bilgisayarlarda önceden yüklenmiş yerel yardım Içeriğini dağıtma
 Çevrimiçi olarak bir bilgisayara bir içerik kümesi yükleyebilir ve sonra bu içerik kümesini diğer bilgisayarlara kopyalayabilirsiniz.

 Gereklilik

- İçerik kümesini yüklediğiniz bilgisayar Internet erişimine sahip olmalıdır.

- Kullanıcılar yüklendikten sonra yerel yardım içeriğini güncelleştirmek, eklemek veya kaldırmak için yönetici haklarına sahip olmalıdır.

  > [!TIP]
  > Kullanıcılar yönetici haklarına sahip değilse, yardım görüntüleyicisinde Içeriği Yönet sekmesini devre dışı bırakmanız önerilir. Daha fazla bilgi için bkz. [Yardım Içerik Yöneticisi geçersiz kılmaları](../ide/help-content-manager-overrides.md).

  Uyarılar

- Kullanıcılar yönetici haklarına sahip değilse, yardım görüntüleyicisinde Içeriği Yönet sekmesini devre dışı bırakmanız önerilir. Daha fazla bilgi için bkz. [Yardım Içerik Yöneticisi geçersiz kılmaları](../ide/help-content-manager-overrides.md).

- Yardım için varsayılan kaynak hala çevrimiçi olmaya devam edecektir.

- İstemcilere, Visual Studio 'nun ilk başlatıldığında temel yardım içeriğini yüklemeleri istenir. Daha fazla bilgi için bkz. [Yardım Içerik Yöneticisi geçersiz kılmaları](../ide/help-content-manager-overrides.md).

### <a name="create-the-content-set"></a>İçerik kümesi oluşturma
 Temel içerik kümesini oluşturabilmeniz için önce hedef bilgisayardaki tüm yerel Visual Studio içeriğini kaldırmanız gerekir.

##### <a name="to-uninstall-local-help"></a>Yerel yardım 'ı kaldırmak için

1. Yardım Görüntüleyicisi 'nde **Içeriği Yönet** sekmesini seçin.

2. **Kullanılabilir belgeler**' in altında, Visual Studio belge kümesine gidin.

3. Her alt öğenin yanındaki **Kaldır** ' ı seçin.

4. Kaldırmak için **Başlat** 'ı seçin

5. *N*: \ProgramData\Microsoft\HelpLibrary2\Catalogs\VisualStudio12 ' e gidin ve klasörün yalnızca catalogType. xml dosyasını içerdiğini doğrulayın.

   Daha önce yüklenmiş olan tüm yerel Visual Studio yardım içeriğini kaldırdıktan sonra, temel içerik kümesini indirmeye hazırlanın.

##### <a name="to-download-the-content"></a>İçeriği indirmek için

1. Yardım Görüntüleyicisi 'nde **Içeriği Yönet** sekmesini seçin.

2. **Kullanılabilir belgeler**' in altında, indirmek istediğiniz belge kümelerine gidin ve **Ekle**' yi seçin.

3. **Başlat**' ı seçin.

   Daha sonra, içeriği istemci bilgisayarlara dağıtılabilmesi için paketlemeyi yapmanız gerekir.

##### <a name="to-package-the-content"></a>İçeriği paketlemek için

1. Daha sonra dağıtım için içeriği kopyalamak üzere bir klasör oluşturun.

     Örneğin: c:\VS12Help.

2. Yönetici izinleriyle cmd. exe ' yi açın.

3. Adım 1 ' de oluşturduğunuz klasöre gidin.

4. Aşağıdakileri yazın:

     Xcopy%SYSTEMDRIVE%\ProgramData\Microsoft\HelpLibrary2 \<*klasöradı*> \/y/e/k/o

     Örneğin: `Xcopy %SYSTEMDRIVE%\ProgramData\Microsoft\HelpLibrary2 c:\VS12Help\ /y /e /k /o`.

### <a name="deploying-the-content"></a>İçeriği dağıtma

##### <a name="to-deploy-the-content"></a>İçeriği dağıtmak için

1. Bir ağ paylaşma oluşturun ve bu konuma Ee yardım içeriğini kopyalayın.

     Örneğin, c:\VS12Help içindeki içeriği \Myserver\vs12help\\ kopyalayın.

2. Yardım içeriği için dağıtım betiğini içeren bir. bat dosyası oluşturun. İstemci, gönderim kapsamında silinmekte olan dosyaların hiçbirinde okuma kilidine sahip olduğundan, güncelleştirmeleri dağıtmadan önce istemcinin kapatılmasını sağlayabilirsiniz.

     Örneğin:

    ```
    REM - copy pre-ripped content to ProgramData
    Xcopy %~dp0HelpLibrary2 %SYSTEMDRIVE%\ProgramData\Microsoft\HelpLibrary2\ /y /e /k /o
    if ERRORLEVEL 1 ECHO *** ERROR COPYING Help Library files to Programdata (%ERRORLEVEL%)

    REM - get processor type and create/run registry update file
    IF "%PROCESSOR_ARCHITECTURE%"=="AMD64" GOTO AMD64

    @echo Architecture type is x86

    ECHO Windows Registry Editor Version 5.00 > x86.reg

    ECHO [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\v2.2\Catalogs] >> x86.reg
    ECHO "ContentStore"="%SYSTEMDRIVE%\\ProgramData\\Microsoft\\HelpLibrary2\\Catalogs\\" >> x86.reg

    ECHO [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\v2.2\Catalogs\VisualStudio12] >> x86.reg
    ECHO "LocationPath"="%SYSTEMDRIVE%\\ProgramData\\Microsoft\\HelpLibrary2\\Catalogs\\VisualStudio12\\"  >> x86.reg
    ECHO "FirstTimeRun"="False"  >> x86.reg

    ECHO [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\v2.2\Catalogs\VisualStudio12\en-US]  >> x86.reg
    ECHO "ContentStore"="%SYSTEMDRIVE%\\ProgramData\\Microsoft\\HelpLibrary2\\Catalogs\\VisualStudio12\\"  >> x86.reg
    ECHO "catalogName"="Visual Studio version Help Documentation"  >> x86.reg

    ECHO [HKEY_LOCAL_MACHINE\Software\Microsoft\VSWinExpress\14.0\help]  >> x86.reg
    ECHO "UseOnlineHelp"=dword:00000000  >> x86.reg

    regedit.exe /s x86.reg
    if ERRORLEVEL 1 ECHO *** ERROR inserting the x86 reg (%ERRORLEVEL%)

    GOTO CONTINUE

    :AMD64
    @echo Architecture type is AMD64

    ECHO Windows Registry Editor Version 5.00 > x64.reg

    ECHO [HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Help\v2.2\Catalogs] >> x64.reg
    ECHO "ContentStore"="%SYSTEMDRIVE%\\ProgramData\\Microsoft\\HelpLibrary2\\Catalogs\\" >> x64.reg

    ECHO [HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Help\v2.2\Catalogs\VisualStudio14] >> x64.reg
    ECHO "LocationPath"="%SYSTEMDRIVE%\\ProgramData\\Microsoft\\HelpLibrary2\\Catalogs\\VisualStudio14\\"  >> x64.reg
    ECHO "FirstTimeRun"="False"  >> x64.reg

    ECHO [HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Help\v2.2\Catalogs\VisualStudio14\en-US]  >> x64.reg
    ECHO "ContentStore"="%SYSTEMDRIVE%\\ProgramData\\Microsoft\\HelpLibrary2\\Catalogs\\VisualStudio12\\en-US\\"  >> x64.reg
    ECHO "catalogName"="Visual Studio version Help Documentation"  >> x64.reg

    ECHO [HKEY_LOCAL_MACHINE\Software\Wow6432Node\Microsoft\VSWinExpress\14.0\help]  >> x64.reg
    ECHO "UseOnlineHelp"=dword:00000000  >> x64.reg

    regedit.exe /s x64.reg
    if ERRORLEVEL 1 ECHO *** ERROR inserting the x64 reg (%ERRORLEVEL%)

    :CONTINUE
    ```

3. Yardım içeriğinin üzerine yükleneceği yerel makinelerde bat dosyasını çalıştırın.

## <a name="see-also"></a>Ayrıca Bkz.
 Yardım Içeriği Yöneticisi [Yardım Içerik Yöneticisi geçersiz kılmaları](../ide/help-content-manager-overrides.md) [Için komut satırı bağımsız değişkenleri](../ide/command-line-arguments-for-the-help-content-manager.md)
