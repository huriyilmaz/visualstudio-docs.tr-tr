---
title: uydu derlemesini isteğe bağlı olarak indirin (ClickOnce apı)
description: Uydu derlemelerini isteğe bağlı olarak nasıl işaretleyeceğinizi ve yalnızca geçerli kültür ayarları için bir istemci makinesi için gereken derlemeyi inditireceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, globalization
- localization, Windows Forms
- Windows Forms, localization
- globalization, ClickOnce
- satellite assemblies, ClickOnce
- ClickOnce deployment, on-demand download
- localization, ClickOnce deployment
- ClickOnce deployment, localization
ms.assetid: fdaa553f-a27e-44eb-a4e2-08c122105a87
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: 1374b409fa8f4f01a521c8e2660020c2e94951f8
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122035585"
---
# <a name="walkthrough-download-satellite-assemblies-on-demand-with-the-clickonce-deployment-api"></a>izlenecek yol: ClickOnce dağıtım apı 'si ile isteğe bağlı uydu derlemelerini indirme
Windows Forms uygulamaları, uydu derlemeleri kullanılarak birden çok kültür için yapılandırılabilir. *Uydu derlemesi* , uygulamanın varsayılan kültürü dışında bir kültür için uygulama kaynakları içeren bir derlemedir.

 [yerellerde ClickOnce uygulamalarda](../deployment/localizing-clickonce-applications.md)anlatıldığı gibi, aynı dağıtımda birden çok kültür için birden çok uydu derlemesi ekleyebilirsiniz [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] . Varsayılan olarak, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Tüm uydu derlemelerini istemci makinesine indirir, ancak tek bir istemci muhtemelen yalnızca bir uydu derlemesi gerektirecektir.

 Bu izlenecek yol, uydu derlemelerinizi isteğe bağlı olarak nasıl işaretleyeceğinizi ve yalnızca geçerli kültür ayarlarına yönelik bir istemci makinesi için gereken derlemeyi nasıl indileceğini gösterir. Aşağıdaki yordam, içinde bulunan araçları kullanır [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)] . Ayrıca, bu görevi ' de gerçekleştirebilirsiniz [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .  ayrıca bkz. [izlenecek yol: tasarımcı veya izlenecek yol ClickOnce dağıtım apı 'si ile isteğe bağlı olarak uydu derlemelerini indirme](/previous-versions/visualstudio/visual-studio-2012/ms366788(v=vs.110)) [: tasarımcıyı kullanarak ClickOnce dağıtım apı 'si ile uydu derlemelerini isteğe](/previous-versions/visualstudio/visual-studio-2013/ms366788(v=vs.120))bağlı olarak indirme.

> [!NOTE]
> Test amacıyla, aşağıdaki kod örneği program aracılığıyla kültürü olarak ayarlar `ja-JP` . Üretim ortamı için bu kodu ayarlama hakkında daha fazla bilgi için bu konunun ilerleyen kısımlarında yer alan "sonraki adımlar" bölümüne bakın.

## <a name="prerequisites"></a>Önkoşullar
 Bu konu, Visual Studio kullanarak uygulamanıza yerelleştirilmiş kaynaklar eklemeyi bildiğinizi varsayar. ayrıntılı yönergeler için bkz. [Walkthrough: yerelWindows forms](/previous-versions/visualstudio/visual-studio-2010/y99d1cd3(v=vs.100)).

### <a name="to-download-satellite-assemblies-on-demand"></a>Uydu derlemelerini isteğe bağlı olarak indirmek için

1. Uydu derlemelerinin isteğe bağlı olarak indirilmesini sağlamak için uygulamanıza aşağıdaki kodu ekleyin.

    :::code language="csharp" source="../snippets/csharp/VS_Snippets_Winforms/ClickOnce.SatelliteAssembliesSDK/CS/Program.cs" id="Snippet1":::
    :::code language="vb" source="../snippets/visualbasic/VS_Snippets_Winforms/ClickOnce.SatelliteAssembliesSDK/VB/Form1.vb" id="Snippet1":::

2. [Resgen.exe (kaynak dosya Oluşturucu)](/dotnet/framework/tools/resgen-exe-resource-file-generator) veya kullanarak uygulamanız için uydu derlemeleri oluşturun [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

3. *MageUI.exe* kullanarak, bir uygulama bildirimi oluşturun veya mevcut uygulama bildiriminizi açın. bu araç hakkında daha fazla bilgi için bkz. [MageUI.exe (Bildirim Oluşturma ve Düzenleme Aracı, grafik istemci)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client).

4. **Dosyalar** sekmesine tıklayın.

5. **Üç nokta** düğmesine (**...**) tıklayın ve *Resgen.exe* kullanarak oluşturduğunuz uydu derlemeleri dahil olmak üzere tüm uygulamanızın derlemelerini ve dosyalarını içeren dizini seçin. (Uydu derlemesi, RFC 1766 biçiminde bir dil tanımlayıcısı olan *\<isoCode>\ApplicationName.resources.dll* biçimde bir ada sahip olacaktır \<isoCode> .)

6. Dosyaları dağıtımınıza eklemek için **doldur** ' a tıklayın.

7. Her uydu derlemesi için **Isteğe bağlı** onay kutusunu seçin.

8. Her uydu derlemesi için Grup alanını ISO dili tanımlayıcısına ayarlayın. Örneğin, Japonca bir uydu derlemesi için bir indirme grubu adı belirtmeniz gerekir `ja-JP` . Bu, kullanıcının özellik ayarına bağlı olarak, adım 1 ' de eklediğiniz kodu uygun uydu derlemesini indirmek üzere etkinleştirir <xref:System.Threading.Thread.CurrentUICulture%2A> .

## <a name="next-steps"></a>Sonraki adımlar
 Bir üretim ortamında, büyük olasılıkla belirli bir değere ayarlanmış olan kod örneğinde satırı kaldırmanız gerekir <xref:System.Threading.Thread.CurrentUICulture%2A> , çünkü istemci makineler varsayılan olarak doğru değere sahip olacaktır. Uygulamanız bir Japonca istemci makinesinde çalıştığında, örneğin, <xref:System.Threading.Thread.CurrentUICulture%2A> `ja-JP` Varsayılan olarak olur. Bu değeri programlı olarak ayarlamak, uygulamanızı dağıtmadan önce uydu derlemelerinizi test etmenin iyi bir yoludur.

## <a name="see-also"></a>Ayrıca bkz.
- [ClickOnce uygulamalarını yerelleştirme](../deployment/localizing-clickonce-applications.md)
