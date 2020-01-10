---
title: Menü öğelerine klavye kısayollarını bağlama | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- keyboard command
- keyboards
- command key
- keyboard shortcuts
- menu items
ms.assetid: 19f483b6-4d3e-424e-9d68-dc129c788e47
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0396d3290ef870fb2c2c7b7b49c774b66397077c
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75852223"
---
# <a name="binding-keyboard-shortcuts-to-menu-items"></a>Menü Öğelerine Klavye Kısayolları Bağlama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir klavye kısayolunu özel bir menü komutuna bağlamak için, Package için. vsct dosyasına bir giriş eklemeniz yeterlidir. Bu konu başlığı altında, klavye kısayolunun özel düğme, menü öğesi veya araç çubuğu komutuna nasıl değiştirileceği ve varsayılan düzenleyicide klavye eşlemesinin nasıl uygulanacağı veya özel bir düzenleyici ile nasıl sınırlandırılacağını açıklanmaktadır.  
  
 Mevcut Visual Studio menü öğelerine klavye kısayolları atamak için bkz. [klavye kısayollarını tanımlama ve özelleştirme](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).  
  
## <a name="choosing-a-key-combination"></a>Anahtar birleşimi seçme  
 Birçok klavye kısayolu, Visual Studio 'da zaten kullanılıyor. Yinelenen bağlamalar algılanabileceğinden ve ayrıca öngörülemeyen sonuçlara neden olabileceğinden, aynı kısayolu birden fazla komuta atamamalısınız. Bu nedenle, bir kısayolu atamadan önce kullanılabilirliğini doğrulamak iyi bir fikirdir.  
  
#### <a name="to-verify-the-availability-of-a-keyboard-shortcut"></a>Klavye kısayolunun kullanılabilirliğini doğrulamak için  
  
1. **Araçlar/Seçenekler/ortam** penceresinde **klavye**' yi seçin.  
  
2. **' De yeni kısayol kullan ' ın** **Global**olarak ayarlandığından emin olun.  
  
3. **Kısayol tuşlarını bas** kutusunda, kullanmak istediğiniz klavye kısayolunu yazın.  
  
    Kısayol zaten Visual Studio 'da kullanılıyorsa, Box **tarafından şu anda kullanılan kısayol** , kısayolun Şu anda çağırdığı komutu gösterir.  
  
4. Eşlenmemiş bir tane bulana kadar anahtarların farklı birleşimlerini deneyin.  
  
   > [!NOTE]
   > ALT kullanan klavye kısayolları, bir menü açabilir ve doğrudan bir komut yürütmez. Bu nedenle, ALT içeren bir kısayol yazdığınızda, **Şu anda Box tarafından kullanılan kısayol** boş olabilir. Kısayolun, **Seçenekler** iletişim kutusunu kapatarak ve ardından tuşlara basarak bir menü açmadığından emin olabilirsiniz.  
  
   Aşağıdaki yordamda, bir menü komutuyla mevcut bir VSPackage olduğunu varsaymaktadır. Bu işlemi gerçekleştirmek için yardıma ihtiyacınız varsa, bir [menü komutuyla uzantı oluşturmaya](../extensibility/creating-an-extension-with-a-menu-command.md)göz atın.  
  
#### <a name="to-assign-a-keyboard-shortcut-to-a-command"></a>Bir komuta klavye kısayolu atamak için  
  
1. Paketiniz için. vsct dosyasını açın.  
  
2. Zaten mevcut değilse, `<Commands>` sonra boş bir `<KeyBindings>` bölümü oluşturun.  
  
   > [!WARNING]
   > Anahtar bağlamaları hakkında daha fazla bilgi için bkz. [KeyBinding](../extensibility/keybinding-element.md).  
  
    `<KeyBindings>` bölümünde, bir `<KeyBinding>` girişi oluşturun.  
  
    `guid` ve `id` özniteliklerini çağırmak istediğiniz komuta ait olanlarla ayarlayın.  
  
    `mod1` özniteliğini **Control**, **alt**veya **SHIFT**olarak ayarlayın.  
  
    KeyBindings bölümü şuna benzemelidir:  
  
   ```xml  
   <KeyBindings>  
       <KeyBinding guid="<name of command set>" id="<name of command id>"  
           editor="guidVSStd97" key1="1" mod1="CONTROL"/>  
   </KeyBindings>  
  
   ```  
  
   Klavye kısayolunuz ikiden fazla anahtar gerektiriyorsa, `mod2` ve `key2` özniteliklerini ayarlayın.  
  
   Çoğu durumda, **kaydırma** ikinci bir değiştirici olmadan kullanılmamalıdır çünkü bu, en fazla alfasayısal anahtarın büyük harf veya simge yazmasına neden olur.  
  
   Sanal anahtar kodları, işlev anahtarları ve **geri al** tuşu gibi kendileriyle ilişkili bir karakter olmayan özel anahtarlara erişmenizi sağlar. Daha fazla bilgi için bkz. [sanal anahtar kodları](https://msdn2.microsoft.com/library/ms645540.aspx).  
  
   Komutu Visual Studio Düzenleyicisi 'nde kullanılabilir hale getirmek için `editor` özniteliğini `guidVSStd97`olarak ayarlayın.  
  
   Komutu yalnızca özel bir düzenleyicide kullanılabilir hale getirmek için, `editor` özniteliğini, özel düzenleyiciyi içeren VSPackage oluşturduğunuzda [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] paket şablonu tarafından oluşturulan özel düzenleyicinin adına ayarlayın. Ad değerini bulmak için, `name` özniteliği "`editorfactory`" olan bir `<GuidSymbol>` düğümü için `<Symbols>` bölümüne bakın. Bu, özel düzenleyicinin adıdır.  
  
## <a name="example"></a>Örnek  
 Bu örnek, CTRL + ALT + C klavye kısayolunu `MyPackage`adlı bir pakette `cmdidMyCommand` adlı bir komuta bağlar.  
  
```  
<CommandTable>  
. . .  
<Commands>  
. . .  
</Commands>  
<KeyBindings>  
  <KeyBinding guid="guidMyPackageCmdSet" id="cmdidMyCommand"   
      key1="C" mod1="CONTROL" mod2="ALT" editor="guidVSStd97" />  
</KeyBindings>  
. . .  
</CommandTable>  
```  
  
## <a name="example"></a>Örnek  
 Bu örnek, CTL + B klavye kısayolunu, `TestEditor`adlı bir projede `cmdidBold` adlı bir komuta bağlar. Komut, diğer düzenleyicilerde değil yalnızca özel düzenleyicide kullanılabilir.  
  
```xml  
<KeyBinding guid="guidVSStd97" id="cmdidBold" editor="guidTestEditorEditorFactory" key1="B" mod1="Control" />  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Menüleri ve Komutlari Genişletme](../extensibility/extending-menus-and-commands.md)
