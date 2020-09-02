---
title: "İzlenecek yol: Tasarımcıyı kullanarak ClickOnce dağıtım API 'SI ile Isteğe bağlı uydu derlemelerini Indirme | Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
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
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 559fb1f3613b42bd2c972f61b45736b07e76a318
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62420025"
---
# <a name="walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer"></a>İzlenecek yol: Tasarımcıyı Kullanarak ClickOnce Dağıtım API'si ile Uydu Derlemelerini İndirme

[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Windows Forms uygulamalar, uydu derlemeleri kullanılarak birden çok kültür için yapılandırılabilir. *Uydu derlemesi* , uygulamanın varsayılan kültürü dışında bir kültür için uygulama kaynakları içeren bir derlemedir.

[ClickOnce uygulamalarını yerelleştirme](../deployment/localizing-clickonce-applications.md)konusunda anlatıldığı gibi, aynı dağıtımda birden çok kültür için birden çok uydu derlemesi dahil edebilirsiniz [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] . Varsayılan olarak, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Tüm uydu derlemelerini istemci makinesine indirir, ancak tek bir istemci muhtemelen yalnızca bir uydu derlemesi gerektirecektir.

Bu izlenecek yol, uydu derlemelerinizi isteğe bağlı olarak nasıl işaretleyeceğinizi ve yalnızca geçerli kültür ayarlarına yönelik bir istemci makinesi için gereken derlemeyi nasıl indileceğini gösterir.

> [!NOTE]
> Test amacıyla, aşağıdaki kod örnekleri program aracılığıyla kültürü olarak ayarlar `ja-JP` . Üretim ortamı için bu kodu ayarlama hakkında daha fazla bilgi için bu konunun ilerleyen kısımlarında yer alan "sonraki adımlar" bölümüne bakın.

### <a name="to-mark-satellite-assemblies-as-optional"></a>Uydu derlemelerini isteğe bağlı olarak işaretlemek için

1. Projenizi yapılandırın. Bu, yerelleştirçalıştığınız tüm kültürler için uydu derlemeleri oluşturur.

2. Çözüm Gezgini ' de proje adına sağ tıklayın ve **Özellikler**' e tıklayın.

3. **Yayımla** sekmesine tıklayın ve ardından **uygulama dosyaları**' na tıklayın.

4. Uydu derlemelerini görüntülemek için **tüm dosyaları göster** onay kutusunu seçin. Varsayılan olarak, tüm uydu derlemeleri dağıtımınıza dahil edilir ve bu iletişim kutusunda görünür olur.

     Uydu bütünleştirilmiş kodu *, ısocode\ApplicationName.resources.dll biçiminde* bir ada sahip olur. burada, *ıSOCODE* , RFC 1766 biçiminde bir dil tanımlayıcısıdır.

5. Her dil tanımlayıcısı için **Indir grup** listesinde **yeni...** öğesine tıklayın. Bir indirme grubu adı istendiğinde, dil tanımlayıcısını girin. Örneğin, bir Japonca uydu derlemesi için, indirme grubu adını belirtmeniz gerekir `ja-JP` .

6. **Uygulama dosyaları** iletişim kutusunu kapatın.

### <a name="to-download-satellite-assemblies-on-demand-in-c"></a>C 'de isteğe bağlı uydu derlemelerini indirmek için\#

1. Program.cs dosyasını açın. Bu dosyayı Çözüm Gezgini görmüyorsanız, projenizi seçin ve **Proje** menüsünde **tüm dosyaları göster**' e tıklayın.

2. Uygun uydu derlemesini indirmek ve uygulamanızı başlatmak için aşağıdaki kodu kullanın.

     [!code-csharp[ClickOnce.SatelliteAssemblies#1](../snippets/csharp/VS_Snippets_Winforms/ClickOnce.SatelliteAssemblies/CS/Program.cs#1)]

### <a name="to-download-satellite-assemblies-on-demand-in-visual-basic"></a>Uydu derlemelerini Visual Basic isteğe bağlı olarak indirmek için

1. Uygulamanın **Özellikler** penceresinde **uygulama** sekmesine tıklayın.

2. Sekme sayfasının alt kısmındaki **uygulama olaylarını görüntüle**' ye tıklayın.

3. Aşağıdaki içeri aktarmaları ApplicationEvents. VB dosyasının başına ekleyin.

     [!code-vb[ClickOnce.SatelliteAssembliesVB#1](../snippets/visualbasic/VS_Snippets_Winforms/ClickOnce.SatelliteAssembliesVB/VB/ApplicationEvents.vb#1)]

4. Sınıfına aşağıdaki kodu ekleyin `MyApplication` .

     [!code-vb[ClickOnce.SatelliteAssembliesVB#2](../snippets/visualbasic/VS_Snippets_Winforms/ClickOnce.SatelliteAssembliesVB/VB/ApplicationEvents.vb#2)]

## <a name="next-steps"></a>Sonraki Adımlar

Bir üretim ortamında, büyük olasılıkla belirli bir değere ayarlanmış kod örneklerinde satırı kaldırmanız gerekir <xref:System.Threading.Thread.CurrentUICulture%2A> , çünkü istemci makineler varsayılan olarak doğru değere sahip olacaktır. Uygulamanız bir Japonca istemci makinesinde çalıştığında, örneğin, <xref:System.Threading.Thread.CurrentUICulture%2A> `ja-JP` Varsayılan olarak olur. Uygulamanızı dağıtmadan önce programlama yoluyla ayarlama, uydu derlemelerinizi test etmenin iyi bir yoludur.

## <a name="see-also"></a>Ayrıca Bkz.

- [İzlenecek yol: ClickOnce Dağıtım API'si ile Uydu Derlemelerini İndirme](../deployment/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api.md)
- [ClickOnce Uygulamalarını Yerelleştirme](../deployment/localizing-clickonce-applications.md)
