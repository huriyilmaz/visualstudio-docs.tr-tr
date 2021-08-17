---
title: Menü öğelerine klavye kısayollarını bağlama | Microsoft Docs
description: Varsayılan düzenleyici veya özel bir düzenleyici için Visual Studio klavye kısayolunu özel düğme, menü öğesi veya araç çubuğu komutuna eşlemeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- keyboard command
- keyboards
- command key
- keyboard shortcuts
- menu items
ms.assetid: 19f483b6-4d3e-424e-9d68-dc129c788e47
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: f9859ee7b280b6861dc7894f1768c0b83261ea23
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122058168"
---
# <a name="bind-keyboard-shortcuts-to-menu-items"></a>Klavye kısayollarını menü öğelerine bağlama
Bir klavye kısayolunu özel bir menü komutuna bağlamak için, Package için *. vsct* dosyasına bir giriş eklemeniz yeterlidir. Bu konu başlığı altında, klavye kısayolunun özel düğme, menü öğesi veya araç çubuğu komutuna nasıl değiştirileceği ve varsayılan düzenleyicide klavye eşlemesinin nasıl uygulanacağı veya özel bir düzenleyici ile nasıl sınırlandırılacağını açıklanmaktadır.

 mevcut Visual Studio menü öğelerine klavye kısayolları atamak için bkz. [klavye kısayollarını tanımlamak ve özelleştirmek](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).

## <a name="choose-a-key-combination"></a>Bir anahtar birleşimi seçin
 Visual Studio çok sayıda klavye kısayolu zaten kullanılıyor. Yinelenen bağlamalar algılanabileceğinden ve ayrıca öngörülemeyen sonuçlara neden olabileceğinden, aynı kısayolu birden fazla komuta atamamalısınız. Bu nedenle, bir kısayolu atamadan önce kullanılabilirliğini doğrulamak iyi bir fikirdir.

### <a name="to-verify-the-availability-of-a-keyboard-shortcut"></a>Klavye kısayolunun kullanılabilirliğini doğrulamak için

1. **Araç**  >  **seçenekleri**  >  **ortamı** penceresinde **klavye**' yi seçin.

2. **' De yeni kısayol kullan ' ın** **Global** olarak ayarlandığından emin olun.

3. **Kısayol tuşlarını bas** kutusunda, kullanmak istediğiniz klavye kısayolunu yazın.

    kısayol zaten Visual Studio kullanılıyorsa, box **tarafından şu anda kullanılan kısayol** , kısayolun şu anda çağırdığı komutu gösterir.

4. Eşlenmemiş bir tane bulana kadar anahtarların farklı birleşimlerini deneyin.

   > [!NOTE]
   > **Alt** kullanan klavye kısayolları, bir menü açabilir ve doğrudan bir komut yürütmez. Bu nedenle, **alt** içeren bir kısayol yazdığınızda, **Şu anda Box tarafından kullanılan kısayol** boş olabilir. Kısayolun, **Seçenekler** iletişim kutusunu kapatarak ve ardından tuşlara basarak bir menü açmadığından emin olabilirsiniz.

   Aşağıdaki yordamda, bir menü komutuyla mevcut bir VSPackage olduğunu varsaymaktadır. Bu işlemi gerçekleştirmek için yardıma ihtiyacınız varsa, bir [menü komutuyla uzantı oluşturma](../extensibility/creating-an-extension-with-a-menu-command.md)konusuna göz atın.

### <a name="to-assign-a-keyboard-shortcut-to-a-command"></a>Bir komuta klavye kısayolu atamak için

1. Paketiniz için *. vsct* dosyasını açın.

2. `<KeyBindings>`Zaten mevcut değilse, boş bir bölüm oluşturun `<Commands>` .

   > [!WARNING]
   > Anahtar bağlamaları hakkında daha fazla bilgi için bkz. [KeyBinding](../extensibility/keybinding-element.md).

    `<KeyBindings>`Bölümünde bir `<KeyBinding>` giriş oluşturun.

    `guid`Ve `id` özniteliklerini çağırmak istediğiniz komuta ait olanlarla ayarlayın.

    `mod1`Özniteliği **Control**, **alt** veya **Shift** olarak ayarlayın.

    KeyBindings bölümü şuna benzemelidir:

   ```xml
   <KeyBindings>
       <KeyBinding guid="<name of command set>" id="<name of command id>"
           editor="guidVSStd97" key1="1" mod1="CONTROL"/>
   </KeyBindings>

   ```

   Klavye kısayolunuz ikiden fazla anahtar gerektiriyorsa, `mod2` ve `key2` özniteliklerini ayarlayın.

   Çoğu durumda, **kaydırma** ikinci bir değiştirici olmadan kullanılmamalıdır çünkü bu, en fazla alfasayısal anahtarın büyük harf veya simge yazmasına neden olur.

   Sanal anahtar kodları, işlev anahtarları ve **geri al** tuşu gibi kendileriyle ilişkili bir karakter olmayan özel anahtarlara erişmenizi sağlar. Daha fazla bilgi için bkz. [sanal anahtar kodları](/windows/desktop/inputdev/virtual-key-codes).

   komutu Visual Studio düzenleyicide kullanılabilir hale getirmek için `editor` özniteliğini olarak ayarlayın `guidVSStd97` .

   Komutu yalnızca özel bir düzenleyicide kullanılabilir hale getirmek için, `editor` [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] özel düzenleyiciyi Içeren VSPackage oluşturduğunuzda özniteliği paket şablonu tarafından oluşturulan özel düzenleyicinin adına ayarlayın. Ad değerini bulmak için, `<Symbols>` `<GuidSymbol>` `name` özniteliği "." ile biten bir düğüm için bölümüne bakın `editorfactory` . Bu, özel düzenleyicinin adıdır.

## <a name="example-1"></a>Örnek 1
 Bu örnek, **CTRL** + **alt** + **C** klavye kısayolunu `cmdidMyCommand` adlı bir pakette adlı bir komuta bağlar `MyPackage` .

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

## <a name="example-2"></a>Örnek 2
 Bu örnek, **CTRL** + **B** klavye kısayolunu adlı bir projede adlı bir komuta bağlar `cmdidBold` `TestEditor` . Komut, diğer düzenleyicilerde değil yalnızca özel düzenleyicide kullanılabilir.

```xml
<KeyBinding guid="guidVSStd97" id="cmdidBold" editor="guidTestEditorEditorFactory" key1="B" mod1="Control" />
```

## <a name="see-also"></a>Ayrıca bkz.
- [Menüleri ve komutları genişletme](../extensibility/extending-menus-and-commands.md)
