---
title: Ayarlar Store | Microsoft Docs
description: Yapılandırma ayarı deposu ve VSPackage ayarları olan verileri okuma hakkında Visual Studio öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Settings Store, using
ms.assetid: 447ec08a-eca5-40b8-89b0-f98fdf3d39a4
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: ed4ee9291539575d1ddb7da31849955ff6d182c6
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122132242"
---
# <a name="using-the-settings-store"></a>Ayarlar Deposu Kullanma
İki tür ayar depoları vardır:

- Salt okunur yapılandırma ayarları ve VSPackage Visual Studio yapılandırma ayarları. Visual Studio tüm bilinen .pkgdef dosyalarından gelen ayarları bu depoda birleştirmektedir.

- Seçenekler iletişim kutusundaki sayfalarda, özellik sayfalarında ve bazı  diğer iletişim kutularında görüntülenenler gibi yazılabilir ayarlar olan kullanıcı ayarları. Visual Studio uzantıları bunları küçük miktarlardaki verilerin yerel depolaması için kullanabilir.

  Bu izlenecek yol, yapılandırma ayarı mağazasından veri okuma adımlarını gösterir. Kullanıcı [ayarları deposuna yazma hakkında bir Ayarlar](../extensibility/writing-to-the-user-settings-store.md) için bkz. User Ayarlar Store'a Yazma.

## <a name="creating-the-example-project"></a>Örnek Project
 Bu bölümde gösterim için bir menü komutuyla basit bir uzantı projesinin nasıl oluşturularak ilgili bilgi ve destek sağ açık edilmektedir.

1. Her Visual Studio uzantısı, uzantı varlıklarını içeren bir VSIX dağıtım projesiyle başlar. adlı [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] bir VSIX projesi `SettingsStoreExtension` oluşturun. VSIX proje şablonunu **Visual C# /** **Genişletilebilirlik Project** Yeni Uygulama iletişim kutusunda bulabilirsiniz.

2. Şimdi **SettingsStoreCommand** adlı özel bir komut öğesi şablonu ekleyin. Yeni Öğe **Ekle iletişim kutusunda** Visual **C# / Genişletilebilirlik'e** gidin ve Özel **Komut'ı seçin.** Pencerenin **en** altındaki Ad alanında, komut dosyası adını **SettingsStoreCommand.cs olarak değiştirin.** Özel komut oluşturma hakkında daha fazla bilgi için bkz. [Menü Komutuyla Uzantı Oluşturma](../extensibility/creating-an-extension-with-a-menu-command.md)

## <a name="using-the-configuration-settings-store"></a>Configuration Ayarlar Store'Ayarlar kullanma
 Bu bölümde yapılandırma ayarlarını algılama ve görüntüleme gösterilir.

1. SettingsStorageCommand.cs dosyasında aşağıdaki using yönergelerini ekleyin:

   ```
   using System.Collections.Generic;
   using Microsoft.VisualStudio.Settings;
   using Microsoft.VisualStudio.Shell.Settings;
   using System.Windows.Forms;
   ```

2. 'de `MenuItemCallback` yönteminin gövdelerini kaldırın ve şu satırları ekleyin, yapılandırma ayarları depolarını elde edin:

   ```
   SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);
   SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration);
   ```

    <xref:Microsoft.VisualStudio.Shell.Settings.ShellSettingsManager>, hizmet üzerinde yönetilen bir yardımcı <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsManager> sınıfıdır.

3. Şimdi Windows Phone Araçları'nın yüklü olup olmadığını bulun. Kod aşağıdaki gibi görünüyor olmalı:

   ```
   private void MenuItemCallback(object sender, EventArgs e)
   {
       SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);
       SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration);
       bool arePhoneToolsInstalled = configurationSettingsStore.CollectionExists(@"InstalledProducts\Microsoft Windows Phone Developer Tools");
       string message = "Microsoft Windows Phone Developer Tools: " + arePhoneToolsInstalled;
       MessageBox.Show(message);
   }
   ```

4. Kodu test etmek. Projeyi derleme ve hata ayıklamayı başlatma.

5. Deneysel örnekte, Araçlar  menüsünde Ayarları ÇağırStoreKomand'a **tıklayın.**

    **Microsoft Windows Phone Geliştirici Araçları: ve ardından** **True** veya False şeklinde bir ileti kutusu **görüyorsanız.**

   Visual Studio sistem kayıt defterindeki ayarları depolar.

#### <a name="to-use-a-registry-editor-to-verify-configuration-settings"></a>Yapılandırma ayarlarını doğrulamak için kayıt defteri düzenleyicisi kullanmak için

1. Yeni Regedit.exe.

2. \\HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0Exp_Config\InstalledProducts.

    > [!NOTE]
    > \14.0Exp_Config\ içeren anahtara bakarak \\ \14.0_Config. Uygulamanın deneysel örneğini Visual Studio, yapılandırma ayarları "14.0Exp_Config" kayıt defteri kovanının içindedir.

3. \Installed Products\ düğümünü genişletin. Önceki adımlarda yer alan **ileti Microsoft Windows Phone Geliştirici Araçları Yüklendi: True** ise \Installed Products\ bir Microsoft Windows Phone Geliştirici Araçları içermesi gerekir. İleti Microsoft Windows Phone Geliştirici Araçları **Yüklendi: False** ise\ \Installed Products\ bir Microsoft Windows Phone Geliştirici Araçları içermez.
