---
title: "İzlenecek yol: ClickOnce dağıtım API 'SI ile Isteğe bağlı derlemeleri Indirme | Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
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
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: af03329a05501427f6d04d6cddbd637c3311b339
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64804950"
---
# <a name="walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api"></a>İzlenecek yol: ClickOnce Dağıtım API'si ile İsteğe Bağlı Derlemeleri İndirme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Varsayılan olarak, uygulama ilk çalıştırıldığında bir uygulamaya dahil edilen tüm derlemeler [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] indirilir. Ancak, uygulamanızın küçük bir kullanıcı kümesi tarafından kullanılan bölümlerine sahip olabilirsiniz. Bu durumda, bir derlemeyi yalnızca türlerinden birini oluştururken indirmek istersiniz. Aşağıdaki izlenecek yol, uygulamanızda belirli derlemelerin "isteğe bağlı" olarak nasıl işaretleneceğini ve <xref:System.Deployment.Application> ortak dil çalışma zamanı (CLR) tarafından talep edildiğinde ad alanındaki sınıfları kullanarak nasıl indirileceğini gösterir.  
  
> [!NOTE]
> Bu yordamı kullanmak için uygulamanızın tam güvende çalışması gerekir.  
  
## <a name="prerequisites"></a>Ön koşullar  
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlerden birine ihtiyacınız olacaktır:  
  
- Windows SDK. Windows SDK, Microsoft Indirme Merkezi ' nden indirilebilir.  
  
- Visual Studio.  
  
## <a name="creating-the-projects"></a>Projeleri oluşturma  
  
#### <a name="to-create-a-project-that-uses-an-on-demand-assembly"></a>İsteğe bağlı derleme kullanan bir proje oluşturmak için  
  
1. ClickOnceOnDemand adlı bir dizin oluşturun.  
  
2. Windows SDK komut Istemi ' ni veya komut Istemi ' ni açın [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
3. ClickOnceOnDemand dizinine geçin.  
  
4. Aşağıdaki komutu kullanarak ortak/özel anahtar çifti oluşturun:  
  
    ```  
    sn -k TestKey.snk  
    ```  
  
5. Not defteri veya başka bir metin düzenleyicisi kullanarak adlı tek bir özelliği olan adlı bir sınıf tanımlayın `DynamicClass` `Message` .  
  
     [!code-csharp[ClickOnceLibrary#1](../snippets/csharp/VS_Snippets_Winforms/ClickOnceLibrary/CS/Class1.cs#1)]
     [!code-vb[ClickOnceLibrary#1](../snippets/visualbasic/VS_Snippets_Winforms/ClickOnceLibrary/VB/Class1.vb#1)]  
  
6. Metni, `ClickOnceLibrary.cs` kullandığınız dile bağlı olarak veya adlı bir dosya olarak `ClickOnceLibrary.vb` ClickOnceOnDemand dizinine kaydedin.  
  
7. Dosyayı bir derlemede derleyin.  
  
    ```csharp  
    csc /target:library /keyfile:TestKey.snk ClickOnceLibrary.cs  
    ```  
  
    ```vb  
    vbc /target:library /keyfile:TestKey.snk ClickOnceLibrary.vb  
    ```  
  
8. Derlemenin ortak anahtar belirtecini almak için aşağıdaki komutu kullanın:  
  
    ```  
    sn -T ClickOnceLibrary.dll  
    ```  
  
9. Metin düzenleyicinizi kullanarak yeni bir dosya oluşturun ve aşağıdaki kodu girin. Bu kod, gerekli olduğunda ClickOnceLibrary derlemesini indiren bir Windows Forms uygulaması oluşturur.  
  
     [!code-csharp[ClickOnceOnDemandCmdLine#1](../snippets/csharp/VS_Snippets_Winforms/ClickOnceOnDemandCmdLine/CS/Form1.cs#1)]
     [!code-vb[ClickOnceOnDemandCmdLine#1](../snippets/visualbasic/VS_Snippets_Winforms/ClickOnceOnDemandCmdLine/VB/Form1.vb#1)]  
  
10. Kodunda, çağrısını bulun <xref:System.Reflection.Assembly.LoadFile%2A> .  
  
11. `PublicKeyToken`Daha önce aldığınız değere ayarlayın.  
  
12. Dosyayı ya da olarak kaydedin `Form1.cs` `Form1.vb` .  
  
13. Aşağıdaki komutu kullanarak bir yürütülebilir dosyaya derleyin.  
  
    ```csharp  
    csc /target:exe /reference:ClickOnceLibrary.dll Form1.cs  
    ```  
  
    ```vb  
    vbc /target:exe /reference:ClickOnceLibrary.dll Form1.vb  
    ```  
  
## <a name="marking-assemblies-as-optional"></a>Derlemeleri Isteğe bağlı olarak işaretleme  
  
#### <a name="to-mark-assemblies-as-optional-in-your-clickonce-application-by-using-mageuiexe"></a>MageUI.exe kullanarak derlemeleri ClickOnce uygulamanızda isteğe bağlı olarak işaretlemek için  
  
1. MageUI.exe kullanarak, [Izlenecek yol: ClickOnce uygulamasını El Ile dağıtma](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)bölümünde açıklandığı gibi bir uygulama bildirimi oluşturun. Uygulama bildirimi için aşağıdaki ayarları kullanın:  
  
    - Uygulama bildirimini adlandırın `ClickOnceOnDemand` .  
  
    - **Dosyalar** sayfasında, ClickOnceLibrary.dll satırında, **dosya türü** sütununu **none**olarak ayarlayın.  
  
    - **Dosyalar** sayfasında, ClickOnceLibrary.dll satırına, `ClickOnceLibrary.dll` **Grup** sütununu yazın.  
  
2. MageUI.exe kullanarak, [Izlenecek yol: ClickOnce uygulamasını El Ile dağıtma](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)bölümünde açıklandığı gibi bir dağıtım bildirimi oluşturun. Dağıtım bildirimi için aşağıdaki ayarları kullanın:  
  
    - Dağıtım bildirimini adlandırın `ClickOnceOnDemand` .  
  
## <a name="testing-the-new-assembly"></a>Yeni derlemeyi test etme  
  
#### <a name="to-test-your-on-demand-assembly"></a>İsteğe bağlı derlemenizi test etmek için  
  
1. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]Dağıtımınızı bir Web sunucusuna yükleyin.  
  
2. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]Dağıtım BILDIRIMINE URL girerek bir Web tarayıcısından ile dağıtılan uygulamanızı başlatın. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]Uygulamanızı çağırırsanız `ClickOnceOnDemand` ve adatum.com kök dizinine YÜKLERSENIZ, URL 'niz şöyle görünür:  
  
    ```  
    http://www.adatum.com/ClickOnceOnDemand/ClickOnceOnDemand.application  
    ```  
  
3. Ana formunuz göründüğünde, ' a basın <xref:System.Windows.Forms.Button> . İleti kutusu penceresinde "Hello, World!" okuyan bir dize görmeniz gerekir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Deployment.Application.ApplicationDeployment>
