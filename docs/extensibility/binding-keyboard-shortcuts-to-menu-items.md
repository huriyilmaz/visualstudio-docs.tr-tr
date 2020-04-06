---
title: Klavye Kısayollarını Menü Öğelerine Bağlama | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- keyboard command
- keyboards
- command key
- keyboard shortcuts
- menu items
ms.assetid: 19f483b6-4d3e-424e-9d68-dc129c788e47
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 94feafbc614be61aaa4eef9e26669c0fbe901ed5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740029"
---
# <a name="bind-keyboard-shortcuts-to-menu-items"></a>Klavye kısayollarını menü öğelerine bağlama
Klavye kısayolu özel bir menü komutuna bağlamak için paket için *.vsct* dosyasına bir giriş eklemeniz yeterlidir. Bu konu, klavye kısayolu özel bir düğme, menü öğesi veya araç çubuğu komutuyla nasıl eşlenir ve varsayılan düzenleyicide klavye eşleciliğini nasıl uygulayacağıveya özel bir düzenleyiciyle nasıl sınırlandırılabildiğini açıklar.

 Varolan Visual Studio menü öğelerine klavye kısayolları atamak için [bkz.](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md)

## <a name="choose-a-key-combination"></a>Anahtar kombinasyonu nu seçin
 Visual Studio'da birçok klavye kısayolları zaten kullanılmaktadır. Yinelenen bağlamaların algıya aşması zor olduğundan ve öngörülemeyen sonuçlara da neden olabileceğinden, aynı kısayolu birden fazla komuta atamamalısınız. Bu nedenle, atamadan önce bir kısayol kullanılabilirliğini doğrulamak için iyi bir fikirdir.

### <a name="to-verify-the-availability-of-a-keyboard-shortcut"></a>Klavye kısayolu kullanılabilirliğini doğrulamak için

1. **Araçlar** > **Seçenekleri** > **Ortamı** penceresinde **Klavye'yi**seçin.

2. **Yeni kısayolu kullan'ın** **Global**olarak ayarlandıklarına emin olun.

3. Basın **kısayolu tuşları** kutusuna, kullanmak istediğiniz klavye kısayolu yazın.

    Kısayol Visual Studio'da zaten **kullanılıyorsa, şu anda kutu tarafından kullanılan Kısayol,** kısayol'un şu anda aradığı komutu gösterir.

4. Eşlenen olmayan bir anahtar bulana kadar farklı tuş kombinasyonlarını deneyin.

   > [!NOTE]
   > **Alt** kullanan klavye kısayolları bir menü açabilir ve doğrudan bir komut uyguluyor olmayabilir. Bu nedenle, **Alt**içeren bir kısayol yazdığınızda şu anda kutu **tarafından kullanılan Kısayol** boş olabilir. **Seçenekler** iletişim kutusunu kapatıp tuşlara basarak kısayol'un menüyü açmadığını doğrulayabilirsiniz.

   Aşağıdaki yordam, menü komutu ile varolan bir VSPackage olduğunu varsayar. Bunu yaparken yardıma ihtiyacınız varsa, [menü komutu ile uzantı oluştur'a](../extensibility/creating-an-extension-with-a-menu-command.md)bir göz atın.

### <a name="to-assign-a-keyboard-shortcut-to-a-command"></a>Bir komuta klavye kısayolu atamak için

1. Paketiniz için *.vsct* dosyasını açın.

2. If'in `<KeyBindings>` zaten mevcut olmadığını söyledikten sonra boş bir bölüm oluşturun. `<Commands>`

   > [!WARNING]
   > Anahtar bağlamalar hakkında daha fazla bilgi için [Keybinding'e](../extensibility/keybinding-element.md)bakın.

    `<KeyBindings>` Bölümde, bir `<KeyBinding>` giriş oluşturun.

    Çağırmak `guid` istediğiniz `id` komutun ve özniteliklerini ayarlayın.

    Özniteliği **Denetim,** Alt veya **Shift**olarak ayarlayın. **Alt** `mod1`

    KeyBindings bölümü aşağıdaki gibi görünmelidir:

   ```xml
   <KeyBindings>
       <KeyBinding guid="<name of command set>" id="<name of command id>"
           editor="guidVSStd97" key1="1" mod1="CONTROL"/>
   </KeyBindings>

   ```

   Klavye kısayolu ikiden fazla tuş gerektiriyorsa, ve `mod2` `key2` öznitelikleri ayarlayın.

   Çoğu durumda, **Shift** ikinci bir değiştirici olmadan kullanılmamalıdır, çünkü basmak zaten çoğu alfasayısal tuşa büyük harf veya sembol yazmaya neden olur.

   Sanal anahtar kodları, işlev tuşları ve **Arka Boşluk** tuşu gibi, onlarla ilişkili bir karaktere sahip olmayan özel tuşlara erişmenizi sağlar. Daha fazla bilgi için [Sanal anahtar kodlarına](/windows/desktop/inputdev/virtual-key-codes)bakın.

   Komutu Visual Studio düzenleyicisinde kullanılabilir hale `editor` getirmek `guidVSStd97`için özniteliği .

   Komutu yalnızca özel bir düzenleyicide kullanılabilir `editor` hale getirmek için, özel düzenleyiciyi içeren [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] VSPackage'ı oluşturduğunuzda Paket Şablonu tarafından oluşturulan özel düzenleyicinin adına özniteliği ayarlayın. Ad değerini bulmak için, `<Symbols>` özniteliği `<GuidSymbol>` " ile `name` `editorfactory`biten bir düğüm için bölüme bakın. Bu özel editörün adıdır.

## <a name="example"></a>Örnek
 Bu örnek, klavye kısayolu **Ctrl**+**Alt**+**C'yi** . adlı `cmdidMyCommand` `MyPackage`bir pakette adlı bir komuta bağlar.

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
 Bu örnek, klavye kısayolu **Ctrl**+**B'yi** . adlı `TestEditor`bir projede adlı `cmdidBold` bir komuta bağlar. Komut, diğer editörlerde değil, yalnızca özel düzenleyicide kullanılabilir.

```xml
<KeyBinding guid="guidVSStd97" id="cmdidBold" editor="guidTestEditorEditorFactory" key1="B" mod1="Control" />
```

## <a name="see-also"></a>Ayrıca bkz.
- [Menüleri ve komutları genişletme](../extensibility/extending-menus-and-commands.md)
