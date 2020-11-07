---
title: ClickOnce tasarımcısını kullanarak uydu derlemesini isteğe bağlı olarak indirme
description: Tasarımcı kullanarak uydu derlemelerini nasıl isteğe bağlı olarak işaretleyeceğinizi ve yalnızca geçerli kültür ayarları için bir istemci makinesi için gereken derlemeyi indireceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Windows Forms, globalization
- ClickOnce deployment, globalization
- localization, Windows Forms
- ClickOnce, on-demand download
- Windows Forms, localization
- ClickOnce deployment, localization
- walkthroughs, localization
ms.assetid: 82b85a47-b223-4221-a17c-38a52c3fb6e2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8b6b57faf01878dc5aff708f0aca47707bf6e48c
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94350341"
---
# <a name="walkthrough-download-satellite-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer"></a>İzlenecek yol: Tasarımcıyı kullanarak ClickOnce dağıtım API 'SI ile uydu derlemelerini isteğe bağlı olarak Indirme
Windows Forms uygulamalar, uydu derlemeleri kullanılarak birden çok kültür için yapılandırılabilir. *Uydu derlemesi* , uygulamanın varsayılan kültürü dışında bir kültür için uygulama kaynakları içeren bir derlemedir.

 [ClickOnce uygulamalarını yerelleştirme](../deployment/localizing-clickonce-applications.md)konusunda anlatıldığı gibi, aynı dağıtımda birden çok kültür için birden çok uydu derlemesi dahil edebilirsiniz [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] . Varsayılan olarak, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Tüm uydu derlemelerini istemci makinesine indirir, ancak tek bir istemci muhtemelen yalnızca bir uydu derlemesi gerektirecektir.

 Bu izlenecek yol, uydu derlemelerinizi isteğe bağlı olarak nasıl işaretleyeceğinizi ve yalnızca geçerli kültür ayarlarına yönelik bir istemci makinesi için gereken derlemeyi nasıl indileceğini gösterir.

> [!NOTE]
> Test amacıyla, aşağıdaki kod örnekleri program aracılığıyla kültürü olarak ayarlar `ja-JP` . Üretim ortamı için bu kodu ayarlama hakkında daha fazla bilgi için bu konunun ilerleyen kısımlarında yer alan "sonraki adımlar" bölümüne bakın.

### <a name="to-mark-satellite-assemblies-as-optional"></a>Uydu derlemelerini isteğe bağlı olarak işaretlemek için

1. Projenizi yapılandırın. Bu, yerelleştirçalıştığınız tüm kültürler için uydu derlemeleri oluşturur.

2. Çözüm Gezgini ' de proje adına sağ tıklayın ve **Özellikler** ' e tıklayın.

3. **Yayımla** sekmesine tıklayın ve ardından **uygulama dosyaları** ' na tıklayın.

4. Uydu derlemelerini görüntülemek için **tüm dosyaları göster** onay kutusunu seçin. Varsayılan olarak, tüm uydu derlemeleri dağıtımınıza dahil edilir ve bu iletişim kutusunda görünür olur.

     Uydu derlemesinin, RFC 1766 biçiminde bir dil tanımlayıcısı olduğu *\<isoCode>\ApplicationName.resources.dll* biçimde adında bir adı olacaktır \<isoCode> .

5. Her dil tanımlayıcısı için **Indirme grubu** listesinde **Yeni** ' ye tıklayın. Bir indirme grubu adı istendiğinde, dil tanımlayıcısını girin. Örneğin, bir Japonca uydu derlemesi için, indirme grubu adını belirtmeniz gerekir `ja-JP` .

6. **Uygulama dosyaları** iletişim kutusunu kapatın.

### <a name="to-download-satellite-assemblies-on-demand-in-c"></a>C 'de isteğe bağlı uydu derlemelerini indirmek için\#

1. *Program.cs* dosyasını açın. Bu dosyayı Çözüm Gezgini görmüyorsanız, projenizi seçin ve **Proje** menüsünde **tüm dosyaları göster** ' e tıklayın.

2. Uygun uydu derlemesini indirmek ve uygulamanızı başlatmak için aşağıdaki kodu kullanın.

     [!code-csharp[ClickOnce.SatelliteAssemblies#1](../deployment/codesnippet/CSharp/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer_1.cs)]

### <a name="to-download-satellite-assemblies-on-demand-in-visual-basic"></a>Uydu derlemelerini Visual Basic isteğe bağlı olarak indirmek için

1. Uygulamanın **Özellikler** penceresinde **uygulama** sekmesine tıklayın.

2. Sekme sayfasının alt kısmındaki **uygulama olaylarını görüntüle** ' ye tıklayın.

3. Aşağıdaki içeri aktarmaları *ApplicationEvents. vb* dosyasının başına ekleyin.

     [!code-vb[ClickOnce.SatelliteAssembliesVB#1](../deployment/codesnippet/VisualBasic/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer_2.vb)]

4. Aşağıdaki kodu `MyApplication` sınıfına ekleyin.

     [!code-vb[ClickOnce.SatelliteAssembliesVB#2](../deployment/codesnippet/VisualBasic/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer_3.vb)]

## <a name="next-steps"></a>Sonraki adımlar
 Bir üretim ortamında, büyük olasılıkla belirli bir değere ayarlanmış kod örneklerinde satırı kaldırmanız gerekir <xref:System.Threading.Thread.CurrentUICulture%2A> , çünkü istemci makineler varsayılan olarak doğru değere sahip olacaktır. Uygulamanız bir Japonca istemci makinesinde çalıştığında, örneğin, <xref:System.Threading.Thread.CurrentUICulture%2A> `ja-JP` Varsayılan olarak olur. Uygulamanızı dağıtmadan önce programlama yoluyla ayarlama, uydu derlemelerinizi test etmenin iyi bir yoludur.

## <a name="see-also"></a>Ayrıca bkz.
- [İzlenecek yol: ClickOnce dağıtım API 'SI ile isteğe bağlı uydu derlemelerini Indirme](../deployment/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api.md)
- [ClickOnce uygulamalarını yerelleştirme](../deployment/localizing-clickonce-applications.md)
