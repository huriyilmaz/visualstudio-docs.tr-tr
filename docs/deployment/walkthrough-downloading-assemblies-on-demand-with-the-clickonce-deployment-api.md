---
title: Derlemeleri isteğe bağlı olarak indirme (ClickOnce API)
description: Uygulama uygulamanıza belirli derlemeleri isteğe ClickOnce olarak işaretlemeyi ve ortak dil çalışma zamanının ihtiyacı olduğunda bunları indirmeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- assemblies, downloading [ClickOnce]
- ClickOnce deployment, on-demand download
- on-demand assemblies, ClickOnce
ms.assetid: d20e2789-8621-4806-b5b7-841122da1456
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: 046d6932e1bfcbc6f0a4b3c60fab96806b4473fd
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122112262"
---
# <a name="walkthrough-download-assemblies-on-demand-with-the-clickonce-deployment-api"></a>Adım adım kılavuz: Derlemeleri isteğe bağlı olarak ClickOnce API'si ile indirme
Varsayılan olarak, bir uygulamaya dahil edilen tüm [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] derlemeler, uygulama ilk kez çalıştırılacaksa indirilir. Ancak, uygulamanın küçük bir kullanıcı kümesi tarafından kullanılan bölümleri olabilir. Bu durumda, bir derlemeyi yalnızca türlerinden birini oluşturmadan indirmek istiyor siniz. Aşağıdaki kılavuzda, uygulamanıza bazı derlemelerin "isteğe bağlı" olarak nasıl işaretlenecekleri ve ortak dil çalışma zamanı (CLR) bunları talep eden ad alanı sınıflarını kullanarak nasıl indirecekleri <xref:System.Deployment.Application> anlatılacaktır.

> [!NOTE]
> Bu yordamı kullanmak için, uygulamanın tam güven içinde çalışması gerekir.

## <a name="prerequisites"></a>Önkoşullar
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlerden biri gerekir:

- Windows SDK'sı. Windows SDK'sı Microsoft İndirme Merkezi'nden indirilebilir.

- Visual Studio.

## <a name="create-the-projects"></a>Projeleri oluşturma

#### <a name="to-create-a-project-that-uses-an-on-demand-assembly"></a>Bir isteğe bağlı derleme kullanan bir proje oluşturmak için

1. ClickOnceOnDemand adlı bir dizin oluşturun.

2. Windows SDK Komut İstemi'ne veya Komut [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] İstemi'ne bakın.

3. ClickOnceOnDemand dizinine tıklayın.

4. Aşağıdaki komutu kullanarak ortak/özel anahtar çifti oluşturma:

   ```cmd
   sn -k TestKey.snk
   ```

5. Bir Not Defteri veya başka bir metin düzenleyicisi kullanarak adlı tek `DynamicClass` bir özelliği olan adlı bir sınıf `Message` tanımlayın.

    :::code language="vb" source="../snippets/visualbasic/VS_Snippets_Winforms/ClickOnceLibrary/VB/Class1.vb" id="Snippet1":::
    :::code language="csharp" source="../snippets/csharp/VS_Snippets_Winforms/ClickOnceLibrary/CS/Class1.cs" id="Snippet1":::

6. Metni, kullandığınız dile bağlı olarak *ClickOnceLibrary.cs* veya *ClickOnceLibrary.vb* adlı bir dosya olarak *ClickOnceOnDemand dizinine* kaydedin.

7. Dosyayı bir derlemede derle.

   ```csharp
   csc /target:library /keyfile:TestKey.snk ClickOnceLibrary.cs
   ```

   ```vb
   vbc /target:library /keyfile:TestKey.snk ClickOnceLibrary.vb
   ```

8. Derlemenin ortak anahtar belirteci almak için aşağıdaki komutu kullanın:

   ```cmd
   sn -T ClickOnceLibrary.dll
   ```

9. Metin düzenleyicinizi kullanarak yeni bir dosya oluşturun ve aşağıdaki kodu girin. Bu kod, Windows ClickOnceLibrary derlemesi indiren bir Windows Forms uygulaması oluşturur.

    :::code language="csharp" source="../snippets/csharp/VS_Snippets_Winforms/ClickOnceOnDemandCmdLine/CS/Form1.cs" id="Snippet1":::
    :::code language="vb" source="../snippets/visualbasic/VS_Snippets_Winforms/ClickOnceOnDemandCmdLine/VB/Form1.vb" id="Snippet1":::

10. Kodda çağrısının yerini <xref:System.Reflection.Assembly.LoadFile%2A> bulun.

11. değerini `PublicKeyToken` daha önce alınan değere ayarlayın.

12. Dosyayı *Form1.cs veya Form1.vb* *olarak kaydedin.*

13. Aşağıdaki komutu kullanarak yürütülebilir dosya olarak derle.

    ```csharp
    csc /target:exe /reference:ClickOnceLibrary.dll Form1.cs
    ```

    ```vb
    vbc /target:exe /reference:ClickOnceLibrary.dll Form1.vb
    ```

## <a name="mark-assemblies-as-optional"></a>Derlemeleri isteğe bağlı olarak işaretleme

#### <a name="to-mark-assemblies-as-optional-in-your-clickonce-application-by-using-mageuiexe"></a>Derlemeleri ClickOnce kullanarak ClickOnce isteğe bağlı olarak işaretlemek MageUI.exe

1. MageUI.exe ** kullanarak, Kılavuz: Bir uygulama bildirimini el ile dağıtma konusunda açıklandığı [gibi ClickOnce oluşturun.](../deployment/walkthrough-manually-deploying-a-clickonce-application.md) Uygulama bildirimi için aşağıdaki ayarları kullanın:

    - Uygulama bildirimine adını `ClickOnceOnDemand` girin.

    - Dosyalar **sayfasındaki** Dosya Türü *ClickOnceLibrary.dll* Hiçbiri **olarak** **ayarlayın.**

    - Dosyalar **sayfasındaki** ClickOnceLibrary.dll `ClickOnceLibrary.dll` sütununa yazın. 

2. Bu *MageUI.exe* kullanarak, Adım adım: Bir uygulamanın el ile dağıtımında açıklandığı [gibi ClickOnce oluşturun.](../deployment/walkthrough-manually-deploying-a-clickonce-application.md) Dağıtım bildirimi için aşağıdaki ayarları kullanın:

    - Dağıtım bildirimini olarak ad `ClickOnceOnDemand` girin.

## <a name="testing-the-new-assembly"></a>Yeni derlemeyi test etme

#### <a name="to-test-your-on-demand-assembly"></a>isteğe bağlı derlemenizi test etmek için

1. Upload [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] web sunucusuna dağıtmanızı sağlar.

2. Dağıtım bildiriminin [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] URL'sini girerek bir Web tarayıcısında ile dağıtılan uygulamanıza başlama. Uygulamanıza çağrı yaptıysanız ve bunu uygulamanın kök dizinine [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] `ClickOnceOnDemand` yükler adatum.com URL'niz şöyle olur:

   ```
   http://www.adatum.com/ClickOnceOnDemand/ClickOnceOnDemand.application
   ```

3. Ana formunuz görüntülendiğinde tuşuna <xref:System.Windows.Forms.Button> basın. İleti kutusu penceresinde "Hello, World!" ifadesini içeren bir dize görüyorsanız.

## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Deployment.Application.ApplicationDeployment>