---
title: İsteğe bağlı derlemeleri indirme (ClickOnce API)
description: ClickOnce uygulamanızdaki belirli derlemeleri isteğe bağlı olarak nasıl işaretleyeceğinizi ve ortak dil çalışma zamanı için gereken durumlarda onları nasıl inditireceğinizi öğrenin.
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fb74d7fd5ad388b9b3dc217bae8782b24517c13b
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94349272"
---
# <a name="walkthrough-download-assemblies-on-demand-with-the-clickonce-deployment-api"></a>İzlenecek yol: ClickOnce dağıtım API 'SI ile isteğe bağlı derlemeleri Indirme
Varsayılan olarak, uygulama ilk çalıştırıldığında bir uygulamaya dahil edilen tüm derlemeler [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] indirilir. Ancak, uygulamanızın küçük bir kullanıcı kümesi tarafından kullanılan bölümlerine sahip olabilirsiniz. Bu durumda, bir derlemeyi yalnızca türlerinden birini oluştururken indirmek istersiniz. Aşağıdaki izlenecek yol, uygulamanızda belirli derlemelerin "isteğe bağlı" olarak nasıl işaretleneceğini ve <xref:System.Deployment.Application> ortak dil çalışma zamanı (CLR) tarafından talep edildiğinde ad alanındaki sınıfları kullanarak nasıl indirileceğini gösterir.

> [!NOTE]
> Bu yordamı kullanmak için uygulamanızın tam güvende çalışması gerekir.

## <a name="prerequisites"></a>Önkoşullar
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlerden birine ihtiyacınız olacaktır:

- Windows SDK. Windows SDK, Microsoft Indirme Merkezi ' nden indirilebilir.

- Visual Studio.

## <a name="create-the-projects"></a>Projeleri oluşturma

#### <a name="to-create-a-project-that-uses-an-on-demand-assembly"></a>İsteğe bağlı derleme kullanan bir proje oluşturmak için

1. ClickOnceOnDemand adlı bir dizin oluşturun.

2. Windows SDK komut Istemi ' ni veya komut Istemi ' ni açın [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

3. ClickOnceOnDemand dizinine geçin.

4. Aşağıdaki komutu kullanarak ortak/özel anahtar çifti oluşturun:

   ```cmd
   sn -k TestKey.snk
   ```

5. Not defteri veya başka bir metin düzenleyicisi kullanarak adlı tek bir özelliği olan adlı bir sınıf tanımlayın `DynamicClass` `Message` .

    [!code-vb[ClickOnceLibrary#1](../deployment/codesnippet/VisualBasic/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api_1.vb)]
    [!code-csharp[ClickOnceLibrary#1](../deployment/codesnippet/CSharp/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api_1.cs)]

6. Metni, kullandığınız dile bağlı olarak *ClickOnceLibrary.cs* veya *ClickOnceLibrary. vb* adlı bir dosya olarak, *ClickOnceOnDemand* dizinine kaydedin.

7. Dosyayı bir derlemede derleyin.

   ```csharp
   csc /target:library /keyfile:TestKey.snk ClickOnceLibrary.cs
   ```

   ```vb
   vbc /target:library /keyfile:TestKey.snk ClickOnceLibrary.vb
   ```

8. Derlemenin ortak anahtar belirtecini almak için aşağıdaki komutu kullanın:

   ```cmd
   sn -T ClickOnceLibrary.dll
   ```

9. Metin düzenleyicinizi kullanarak yeni bir dosya oluşturun ve aşağıdaki kodu girin. Bu kod, gerekli olduğunda ClickOnceLibrary derlemesini indiren bir Windows Forms uygulaması oluşturur.

     [!code-csharp[ClickOnceOnDemandCmdLine#1](../deployment/codesnippet/CSharp/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api_2.cs)]
     [!code-vb[ClickOnceOnDemandCmdLine#1](../deployment/codesnippet/VisualBasic/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api_2.vb)]

10. Kodunda, çağrısını bulun <xref:System.Reflection.Assembly.LoadFile%2A> .

11. `PublicKeyToken`Daha önce aldığınız değere ayarlayın.

12. Dosyayı *Form1.cs* veya *Form1. vb* olarak kaydedin.

13. Aşağıdaki komutu kullanarak bir yürütülebilir dosyaya derleyin.

    ```csharp
    csc /target:exe /reference:ClickOnceLibrary.dll Form1.cs
    ```

    ```vb
    vbc /target:exe /reference:ClickOnceLibrary.dll Form1.vb
    ```

## <a name="mark-assemblies-as-optional"></a>Derlemeleri isteğe bağlı olarak işaretle

#### <a name="to-mark-assemblies-as-optional-in-your-clickonce-application-by-using-mageuiexe"></a>MageUI.exe kullanarak derlemeleri ClickOnce uygulamanızda isteğe bağlı olarak işaretlemek için

1. *MageUI.exe* kullanarak, [Izlenecek yol: ClickOnce uygulamasını el ile dağıtma](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)bölümünde açıklandığı gibi bir uygulama bildirimi oluşturun. Uygulama bildirimi için aşağıdaki ayarları kullanın:

    - Uygulama bildirimini adlandırın `ClickOnceOnDemand` .

    - **Dosyalar** sayfasında, *ClickOnceLibrary.dll* satırında, **dosya türü** sütununu **none** olarak ayarlayın.

    - **Dosyalar** sayfasında, *ClickOnceLibrary.dll* satırına, `ClickOnceLibrary.dll` **Grup** sütununu yazın.

2. *MageUI.exe* kullanarak, [Izlenecek yol: ClickOnce uygulamasını el ile dağıtma](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)bölümünde açıklandığı gibi bir dağıtım bildirimi oluşturun. Dağıtım bildirimi için aşağıdaki ayarları kullanın:

    - Dağıtım bildirimini adlandırın `ClickOnceOnDemand` .

## <a name="testing-the-new-assembly"></a>Yeni derlemeyi test etme

#### <a name="to-test-your-on-demand-assembly"></a>İsteğe bağlı derlemenizi test etmek için

1. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]Dağıtımınızı bir Web sunucusuna yükleyin.

2. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]Dağıtım BILDIRIMINE URL girerek bir Web tarayıcısından ile dağıtılan uygulamanızı başlatın. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]Uygulamanızı çağırırsanız `ClickOnceOnDemand` ve adatum.com kök dizinine YÜKLERSENIZ, URL 'niz şöyle görünür:

   ```
   http://www.adatum.com/ClickOnceOnDemand/ClickOnceOnDemand.application
   ```

3. Ana formunuz göründüğünde, ' a basın <xref:System.Windows.Forms.Button> . İleti kutusu penceresinde "Hello, World!" okuyan bir dize görmeniz gerekir.

## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Deployment.Application.ApplicationDeployment>