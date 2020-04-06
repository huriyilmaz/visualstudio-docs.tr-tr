---
title: Ayarlar Deposunu Kullanma | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Settings Store, using
ms.assetid: 447ec08a-eca5-40b8-89b0-f98fdf3d39a4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b3bbc09586f883e067e32f525a0331c1a9e253f5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698512"
---
# <a name="using-the-settings-store"></a>Ayarlar Deposu Kullanma
İki tür ayar vardır:

- Salt okunur Visual Studio ve VSPackage ayarları olan yapılandırma ayarları. Visual Studio, bilinen tüm .pkgdef dosyalarının ayarlarını bu mağazada birleştirir.

- **Seçenekler** iletişim kutusundaki sayfalarda, özellik sayfalarında ve diğer bazı iletişim kutularında görüntülenen ayarlar gibi yazılabilir ayarlar olan kullanıcı ayarları. Visual Studio uzantıları bunları küçük miktarlardaki verilerin yerel depolaması için kullanabilir.

  Bu gözden geçirme, yapılandırma ayar deposundaki verilerin nasıl okunduğunu gösterir. [Kullanıcı ayarları deposuna](../extensibility/writing-to-the-user-settings-store.md) nasıl yazılanın nasıl yazıldığına ilişkin bir açıklama için Kullanıcı Ayarları Mağazası'na yazma bölümüne bakın.

## <a name="creating-the-example-project"></a>Örnek Proje Oluşturma
 Bu bölümde, gösteri için bir menü komutu ile basit bir uzantı projesi oluşturmak için nasıl gösterir.

1. Her Visual Studio uzantısı, uzantı varlıklarını içeren bir VSIX dağıtım projesiyle başlar. Adlı `SettingsStoreExtension` [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] bir VSIX projesi oluşturun. **Visual C# / Genişletilebilirlik**altında **Yeni Proje** iletişim kutusunda VSIX proje şablonu bulabilirsiniz.

2. Şimdi **SettingsStoreCommand**adlı özel bir komut öğesi şablonu ekleyin. Yeni **Öğe Ekle** iletişim kutusunda Visual **C# / Genişletilebilirlik'e** gidin ve **Özel Komut'u**seçin. Pencerenin altındaki **Ad** alanında, komut dosyası adını **SettingsStoreCommand.cs**olarak değiştirin. Özel komut oluşturma hakkında daha fazla bilgi için [Menü Komutu yla Uzantı Oluşturma'ya](../extensibility/creating-an-extension-with-a-menu-command.md) bakın

## <a name="using-the-configuration-settings-store"></a>Yapılandırma Ayarları Deposu'nu kullanma
 Bu bölümde, yapılandırma ayarlarının nasıl algılanıp görüntülenenegösterilmektedir.

1. SettingsStorageCommand.cs dosyasına, yönergeleri kullanarak aşağıdakileri ekleyin:

   ```
   using System.Collections.Generic;
   using Microsoft.VisualStudio.Settings;
   using Microsoft.VisualStudio.Shell.Settings;
   using System.Windows.Forms;
   ```

2. In, `MenuItemCallback`yöntemin gövdesini kaldırmak ve bu satırları eklemek yapılandırma ayarları deposu olsun:

   ```
   SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);
   SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration);
   ```

    Hizmet <xref:Microsoft.VisualStudio.Shell.Settings.ShellSettingsManager> üzerinde <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsManager> yönetilen bir yardımcı sınıftır.

3. Şimdi Windows Phone Araçları'nın yüklü olup olmadığını öğrenin. Kod şu na benzemelidir:

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

4. Kodu test edin. Projeyi oluşturun ve hata ayıklamaya başlayın.

5. Deneysel örnekte, **Araçlar** menüsünde, **Invoke SettingsStoreCommand'ı**tıklatın.

    Microsoft Windows Phone Geliştirici Araçları'nı belirten bir ileti kutusu görmeniz **gerekir:** ardından **True** or **False**.

   Visual Studio, sistem kayıt defterinde ayarlar deposunu tutar.

#### <a name="to-use-a-registry-editor-to-verify-configuration-settings"></a>Yapılandırma ayarlarını doğrulamak için bir kayıt defteri düzenleyicisi kullanmak için

1. Regedit.exe'yi aç.

2. HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0Exp_Config\InstalledProducts'e\\gidin.

    > [!NOTE]
    > \14.0Exp_Config\ içeren ve \14.0_Config'i\\içermeyen anahtara baktığından emin olun. Visual Studio'nun deneysel örneğini çalıştırdığınızda, yapılandırma ayarları kayıt defteri kovanında "14.0Exp_Config" şeklindedir.

3. \Yüklü Ürünler\ düğümündeki nigenişletin. Önceki adımlardaki ileti **Microsoft Windows Phone Geliştirici Araçları Yüklüyse: True**, sonra \Installed Products\ bir Microsoft Windows Phone Geliştirici Araçları düğümü içermelidir. İleti Microsoft **Windows Phone Geliştirici Araçları Yüklü ise: False**, sonra \Installed Products\ bir Microsoft Windows Phone Geliştirici Araçları düğüm içermemelidir.
