---
title: Yalıtılmış Kabuğu özelleştirme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio shell, isolated mode
ms.assetid: e0b7c3ae-210f-4f48-ac49-6a59e6034f5f
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 724d4d0c4b392a362e702f33ea996df3a6fc0ad6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62555977"
---
# <a name="customizing-the-isolated-shell"></a>Yalıtılmış Kabuğu Özelleştirme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio Kullanıcı arabiriminin farklı yönlerini değiştirerek ve özelleştirilmiş uygulamanıza dahil olan komutları ve özellikleri kısıtlayarak, Visual Studio yalıtılmış Kabuk uygulamanızı özelleştirebilirsiniz.  
  
## <a name="using-the-applicationpkgdef-file"></a>Application. pkgdef dosyasını kullanma  
 Yalıtılmış Kabuk şablonu çözümü bir *SolutionName*içerir. Aşağıdaki özellikleri değiştirmenize olanak sağlayan Application. pkgdef dosyası:  
  
##### <a name="the-application-title"></a>Uygulama başlığı  
 *SolutionName*Içindeki "AppName" satırının değerini değiştirerek, uygulamanın başlık çubuğunda görüntülenen ad olan uygulama başlığını özelleştirmeniz gerekir. Application. pkgdef dosyası. Daha ayrıntılı bilgi için bkz. [Izlenecek yol: temel yalıtılmış Kabuk uygulaması oluşturma](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
 Uygulama başlığının Şu anda yüklü olan projeyi görüntülemesini istemiyorsanız, *SolutionName*Içindeki "ShowHierarchyRootInTitle" satırının değerini değiştirin. DWORD: 00000001 'den DWORD: 00000000 ' ya uygulama. pkgdef dosyası.  
  
##### <a name="the-application-icon"></a>Uygulama simgesi  
 Uygulama başlık çubuğunda uygulama adı tarafından görüntülenen simge olan uygulama simgesini özelleştirebilirsiniz. Simge dizinine farklı bir simge kopyalayın. **Çözüm Gezgini**, simgesini kaynak dosyaları klasörüne ekleyin. Ardından VSShellStub. rc dosyasını açın ve IDI_STUBPROGRAM değerini yeni simgenin adıyla değiştirin. Daha ayrıntılı bilgi için bkz. [Izlenecek yol: temel yalıtılmış Kabuk uygulaması oluşturma](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
##### <a name="the-command-line-logo"></a>Komut satırı logosu  
 *Çözüm adı*Içindeki "CommandLineLogo" satırının değerini değiştirerek, uygulama komut satırından başlatıldığında görüntülenen metin olan komut satırı logosunu özelleştirebilirsiniz. Application. pkgdef dosyası. Daha ayrıntılı bilgi için bkz [. Izlenecek yol: temel yalıtılmış Kabuk uygulaması oluşturma](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)  
  
##### <a name="the-name-of-the-user-files-subfolder"></a>Kullanıcı dosyaları alt klasörünün adı  
 *SolutionName*Içindeki "Userfilessubklasöradı" satırının değerini değiştirerek, uygulamanızın kullanıcı dosyaları için sakladığı klasörün adını değiştirebilirsiniz. Application. pkgdef dosyası.  
  
##### <a name="the-title-of-the-solution-tree-node-in-the-new-project-dialog"></a>Yeni proje iletişim kutusundaki çözüm ağacı düğümünün başlığı  
 Yeni proje iletişim kutusundaki çözüm düğümünün başlığını, *SolutionName*Içindeki "Newprojdlslntreenodetitle" satırının değerini değiştirerek özelleştirebilirsiniz. Application. pkgdef dosyası.  
  
##### <a name="the-installed-templates-header-in-the-new-project-dialog"></a>Yeni proje iletişim kutusunda yüklü şablonlar üst bilgisi  
 Yeni proje iletişim kutusunda yüklü şablonlar başlığını, *SolutionName*Içindeki "Newprojdlınstalınstalınstalınstalstkıdr" satırının değerini değiştirerek değiştirebilirsiniz. Application. pkgdef dosyası.  
  
##### <a name="whether-or-not-to-hide-miscellaneous-files-by-default"></a>Çeşitli dosyaların varsayılan olarak gizlenmesi veya gizlenmeyeceğini belirtir  
 *SolutionName*Içindeki "HideMiscellaneousFilesByDefault" satırının değerini değiştirerek, çeşitli dosyaların varsayılan olarak gizlenmesi isteyip istemediğinizi belirtebilirsiniz. Application. pkgdef dosyası. Çeşitli dosyaları gizlemek için değeri ayarlayın `dword:00000001` ve dosyaları göstermek için değeri ayarlayın `dword:00000000` .  
  
##### <a name="whether-or-not-to-disable-the-output-window"></a>Çıkış penceresinin devre dışı bırakılıp başlatılmayacağını belirtir  
 *SolutionName*Içindeki "DisableOutputWindow" satırının değerini değiştirerek, uygulamanızda çıkış penceresinin devre dışı bırakılıp bırakılmayacağını belirtebilirsiniz. Application. pkgdef dosyası. Çıkış penceresini devre dışı bırakmak için değeri ayarlayın `dword:00000001` ve çıkış penceresini göstermek için değeri ayarlayın `dword:00000000` .  
  
##### <a name="whether-or-not-to-allow-dropped-files-on-the-main-window"></a>Ana pencerede bırakılan dosyaların izin verilip verilmeyeceğini belirtir  
 *SolutionName*Içindeki "AllowsDroppedFilesOnMainWindow" satırının değerini değiştirerek, uygulamanızda ana pencerede bırakılan dosyalara izin verilip verilmeyeceğini belirtebilirsiniz. Application. pkgdef dosyası. Bırakılan dosyalara izin vermek için, değeri ayarlayın `dword:00000001` ve bırakılan dosyalara izin vermemek için değeri ayarlayın `dword:00000000` .  
  
##### <a name="the-default-search-page"></a>Varsayılan arama sayfası  
 Web tarayıcı penceresi açıldığında, *SolutionName*Içindeki "DefaultSearchPage" satırının değerini değiştirerek görüntülenen sayfa olan Web tarayıcısı sayfasını özelleştirebilirsiniz. Application. pkgdef dosyası.  
  
##### <a name="the-default-home-page"></a>Varsayılan giriş sayfası  
 *SolutionName*Içindeki "DefaultHomePage" satırının değerini değiştirerek giriş sayfasını özelleştirebilirsiniz. Application. pkgdef dosyası. Daha ayrıntılı bilgi için bkz [. Izlenecek yol: temel yalıtılmış Kabuk uygulaması oluşturma](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)  
  
##### <a name="whether-or-not-to-hide-the-solution-concept"></a>Çözüm kavramının gizlenmesi veya gizlenmeyeceğini belirtir  
 *SolutionName*Içindeki "Hidesolutionkavram" satırının değerini değiştirerek çözümün uygulamanızda gizlenmesi gerekip gerekmediğini belirtebilirsiniz. Application. pkgdef dosyası. Çözümü gizlemek için değeri ayarlayın `dword:00000001` ve çözümü göstermek için değeri ayarlayın `dword:00000000` .  
  
##### <a name="the-default-debug-engine"></a>Varsayılan hata ayıklama altyapısı  
 *SolutionName*Içindeki "DefaultDebugEngine" satırının değerini değiştirerek uygulamanızın kullandığı hata ayıklama altyapısını değiştirebilirsiniz. Hata ayıklama altyapılarınızın GUID 'INE Application. pkgdef dosyası.  
  
##### <a name="the-file-extension-of-the-user-options-file"></a>Kullanıcı seçenekleri dosyasının dosya uzantısı  
 *SolutionName*Içindeki "UserOptsFileExt" satırının değerini değiştirerek, uygulamanızın kullanıcı dosyaları için sakladığı klasörün adını değiştirebilirsiniz. Application. pkgdef dosyası.  
  
##### <a name="the-solution-file-extension"></a>Çözüm dosyası uzantısı  
 Çözüm dosyalarınız için kullanılan uzantıyı, *SolutionName*Içindeki "SolutionFileExt" satırının değerini değiştirerek değiştirebilirsiniz. Application. pkgdef dosyası.  
  
##### <a name="the-default-user-files-folder-root"></a>Varsayılan Kullanıcı dosyaları klasör kökü  
 *SolutionName*Içindeki "Userfilessubklasöradı" satırının değerini değiştirerek, uygulamanız için Kullanıcı dosyalarının kök klasörünün adını değiştirebilirsiniz. Application. pkgdef dosyası.  
  
##### <a name="the-solution-file-creator-identifier"></a>Çözüm dosyası Oluşturucu tanımlayıcısı  
 Çözüm dosyalarınızda kullanılan tanımlayıcıyı, *SolutionName*Içindeki "SolutionFileCreatorIdentifier" satırının değerini değiştirerek değiştirebilirsiniz. Application. pkgdef dosyası.  
  
##### <a name="the-default-projects-location"></a>Varsayılan proje konumu  
 *SolutionName*Içindeki "DefaultProjectsLocation" satırının değerini değiştirerek varsayılan projeler konumunun adını değiştirebilirsiniz. Application. pkgdef dosyası.  
  
##### <a name="the-application-localization-package"></a>Uygulama yerelleştirme paketi  
 *SolutionName*Içindeki "AppLocalizationPackage" satırının değerini değiştirerek, uygulamanız için kullanılan yerelleştirme paketini değiştirebilirsiniz. Application. pkgdef dosyası.  
  
##### <a name="whether-or-not-to-show-the-hierarchy-root-in-the-title"></a>Başlıkta hiyerarşi kökünün gösterilip gösterilmeyeceğini belirtir  
 *SolutionName*Içindeki "ShowHierarchyRootInTitle" satırının değerini değiştirerek, uygulamanızın başlık çubuğunda hiyerarşi kökünün gösterilip gösterilmeyeceğini belirtebilirsiniz. Application. pkgdef dosyası. Hiyerarşi kökünü göstermek için değeri ayarlayın `dword:00000001` ve hiyerarşi kökünü gizlemek için değeri ayarlayın `dword:00000000` .  
  
##### <a name="specifying-a-start-page"></a>Başlangıç sayfası belirtme  
 Özel uygulamanız için bir başlangıç sayfası seçin, *SolutionName*. Application. pkgdef dosyası, "DisableStartPage" değerini olarak ayarlayın `dword:00000000` ve `[$RootKey$\StartPage\Default]` URI 'yi. xaml dosyasının konumuna ayarlayın:  
  
```  
DisableStartPage=dword:00000000  
[$RootKey$\StartPage\Default]  
"Uri"="$RootFolder$\<name of XAML file>"  
```  
  
 *SolutionName*Kullanıcı arabirimi projesindeki ApplicationCommands. vsct dosyasında, "No_ShellPkg_startPageCommand" girişini not edin:  
  
```  
<!--<Define name="No_ShellPkg_StartPageCommand"/>-->  
```  
  
 . Xaml dosyasını ve ihtiyacınız olan tüm grafik dosyalarını *SolutionName* projesine eklemeniz gerekir. Bu dosyalar, başka bir dizinden eklenmediği için gerçekten *SolutionName* proje dizinine kopyalanmalıdır.  
  
 Dosyaların *$RootFolder $* dizinine kopyalanabilmesi için tüm dosyalarda **öğe türü** özelliğini **yalıtılmış Kabuk dosyası** olarak ayarlayın. ( **Öğe türü** özelliğini ayarlamak için, dosyaya sağ tıklayın ve **Özellikler**' i seçin. Bu özellik, **genel** **yapılandırma özellikleri**altında bulunur.)  
  
 Başlangıç sayfalarını özelleştirme hakkında daha fazla bilgi için, bkz. [Başlangıç sayfasını özelleştirme](../ide/customizing-the-start-page-for-visual-studio.md).  
  
## <a name="using-other-elements-of-the-isolated-shell"></a>Yalıtılmış kabuğun diğer öğelerini kullanma  
 Uygulamanızı daha fazla özelleştirmek için yalıtılmış Kabuk çözüm şablonuna dahil edilen diğer dosya ve projeleri kullanabilirsiniz.  
  
##### <a name="enabledisable-visual-studio-packages"></a>Visual Studio paketlerini etkinleştir/devre dışı bırak  
 *SolutionName*. pkgundef dosyası belirli paketleri dışlayarak belirli türdeki Visual Studio işlevlerini devre dışı bırakmanızı sağlar. Örneğin, aşağıdaki satır:  
  
```  
[$RootKey$\Projects\{A2FE74E1-B743-11d0-AE1A-00A0C90FFFC3}\AddItemTemplates\TemplateDirs\{39c9c826-8ef8-4079-8c95-428f5b1c323f}]  
```  
  
 **Yeni proje** iletişim kutusunda görünen proje şablonları kümesinden çeşitli dosyalar projesini kaldırır. Daha ayrıntılı bilgi için bkz. [Izlenecek yol: temel yalıtılmış Kabuk uygulaması oluşturma](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
##### <a name="enabledisable-menu-commands"></a>Menü komutlarını etkinleştir/devre dışı bırak  
 *SolutionName*UI. vsct dosyası yalıtılmış kabuğun kullanabildiği tüm menü komutlarının açıklamalı bir listesini içerir. Verilen bir komutu devre dışı bırakmak için karşılık gelen satırın açıklamasını kaldırın. Örneğin, pencere/bölünmüş yorumu devre dışı bırakmak için satırın açıklamasını kaldırın `<Define name="No_SplitCommand"/>` . Daha ayrıntılı bilgi için bkz. [Izlenecek yol: temel yalıtılmış Kabuk uygulaması oluşturma](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
##### <a name="the-bitmap-used-on-the-splash-screen"></a>Giriş ekranında kullanılan bit eşlem  
 Uygulama başlatıldığında görüntülenen ve *SolutionName*Içindeki "SplashScreenBitmap" satırının değerini değiştirerek, giriş ekranında kullanılan bit eşlemi özelleştirebilirsiniz. Application. pkgdef dosyası. Daha ayrıntılı bilgi için bkz. [Izlenecek yol: temel yalıtılmış Kabuk uygulaması oluşturma](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
##### <a name="the-helpabout-window"></a>Yardım/hakkında penceresi  
 Yalıtılmış Kabuk şablonunda, uygulamanız için yardım/hakkında kutusunu özelleştirmek üzere kullanabileceğiniz ayrı bir proje vardır. Daha ayrıntılı bilgi için bkz. [Izlenecek yol: temel yalıtılmış Kabuk uygulaması oluşturma](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).
