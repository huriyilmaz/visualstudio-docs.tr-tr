---
title: Tasarımcıyı kullanarak isteğe bağlı derlemeleri indirme (ClickOnce API)
description: Tasarımcı'ı kullanarak uygulama uygulamanıza ClickOnce derlemeleri isteğe bağlı olarak işaretlemeyi ve ortak dil çalışma zamanının ihtiyacı olduğunda bunları indirmeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- assemblies, downloading [ClickOnce]
- Windows applications, ClickOnce deployments
- ClickOnce deployment, on-demand download
- on-demand assemblies, ClickOnce
ms.assetid: 59a0dd5f-1cab-4f2f-b780-0ab7399905d5
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: 1b55cb3ce52864d8649008cd5f4f187c170c5813
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725373"
---
# <a name="walkthrough-download-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer"></a>Adım adım kılavuz: Tasarımcıyı kullanarak ClickOnce dağıtım API'si ile isteğe bağlı derlemeleri indirme
Varsayılan olarak, bir uygulamaya dahil edilen tüm [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] derlemeler, uygulama ilk kez çalıştırılana kadar indirilir. Ancak, uygulamanın küçük bir kullanıcı kümesi tarafından kullanılan bölümleri olabilir. Bu durumda, bir derlemeyi yalnızca türlerinden birini oluşturmadan indirmek istiyor. Aşağıdaki kılavuzda, uygulamanıza bazı derlemelerin "isteğe bağlı" olarak nasıl işaretlenecekleri ve ortak dil çalışma zamanı talep olduğunda ad alanı sınıflarını kullanarak nasıl <xref:System.Deployment.Application> indirecekleri anlatılacaktır.

> [!NOTE]
> Bu yordamı kullanmak için, uygulamanın tam güven içinde çalışması gerekir.

> [!NOTE]
> Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için Araçlar menüsünde İçeri **ve Dışarı Ayarlar'ye** tıklayın.  Daha fazla bilgi için [bkz. Ayarları sıfırlama.](../ide/environment-settings.md#reset-settings)

## <a name="create-the-projects"></a>Projeleri oluşturma

### <a name="to-create-a-project-that-uses-an-on-demand-assembly-with-visual-studio"></a>Visual Studio ile isteğe bağlı derleme kullanan bir proje Visual Studio

1. içinde yeni Windows Forms projesi [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] oluşturun. Dosya menüsünde **Ekle'nin** üzerine **gelin ve** ardından Yeni Dosya'ya **Project.** İletişim **kutusunda bir Sınıf** Kitaplığı projesi seçin ve olarak ad `ClickOnceLibrary` girin.

   > [!NOTE]
   > Bu Visual Basic, proje özelliklerini değiştirerek bu projenin kök ad alanını tercih edilen ad alanı olarak veya olarak `Microsoft.Samples.ClickOnceOnDemand` değiştirmenizi öneririz. Kolaylık olması için bu kılavuzda yer alan iki proje aynı ad alanı içindedir.

2. adlı tek bir özelliği `DynamicClass` olan adlı bir sınıf `Message` tanımlayın.

    :::code language="vb" source="../snippets/visualbasic/VS_Snippets_Winforms/ClickOnceLibrary/VB/Class1.vb" id="Snippet1":::
    :::code language="csharp" source="../snippets/csharp/VS_Snippets_Winforms/ClickOnceLibrary/CS/Class1.cs" id="Snippet1":::

3. içinde Windows Forms **projesini Çözüm Gezgini.** Derlemeye bir başvuru <xref:System.Deployment.Application> ve projeye bir proje başvurusu `ClickOnceLibrary` ekleyin.

   > [!NOTE]
   > Bu Visual Basic, proje özelliklerini değiştirerek bu projenin kök ad alanını tercih edilen ad alanı olarak veya olarak `Microsoft.Samples.ClickOnceOnDemand` değiştirmenizi öneririz. Kolaylık olması için bu kılavuzda yer alan iki proje aynı ad alanına yer almaktadır.

4. Forma sağ tıklayın, **menüden** Kodu Görüntüle'ye tıklayın ve forma aşağıdaki başvuruları ekleyin.

    :::code language="csharp" source="../snippets/csharp/VS_Snippets_Winforms/ClickOnceOnDemand/CS/Form1.cs" id="Snippet1":::
    :::code language="vb" source="../snippets/visualbasic/VS_Snippets_Winforms/ClickOnceOnDemand/VB/Form1.vb" id="Snippet1":::

5. Bu derlemeyi isteğe bağlı olarak indirmek için aşağıdaki kodu ekleyin. Bu kod, genel bir sınıf kullanarak bir derleme kümesiyle grup adı eşlemeyi <xref:System.Collections.DictionaryBase.Dictionary%2A> gösterir. Bu kılavuzda yalnızca tek bir derleme indireceğimiz için, grubumuzda yalnızca bir derleme var. Gerçek bir uygulamada, uygulamanıza tek bir özellikle ilgili tüm derlemeleri aynı anda indirmeniz olasıdır. Eşleme tablosu, bir özelente ait olan tüm URL'leri bir indirme grubu adıyla bağ bağarak bunu kolayca yapabilirsiniz.

    :::code language="csharp" source="../snippets/csharp/VS_Snippets_Winforms/ClickOnceOnDemand/CS/Form1.cs" id="Snippet2":::
    :::code language="vb" source="../snippets/visualbasic/VS_Snippets_Winforms/ClickOnceOnDemand/VB/Form1.vb" id="Snippet2":::

6. Görünüm menüsünde **Araç** **Kutusu'na tıklayın.** Araç <xref:System.Windows.Forms.Button> Kutusundan **forma** bir sürükleyin. Düğmeye çift tıklayın ve olay işleyiciye aşağıdaki <xref:System.Windows.Forms.Control.Click> kodu ekleyin.

    :::code language="csharp" source="../snippets/csharp/VS_Snippets_Winforms/ClickOnceOnDemand/CS/Form1.cs" id="Snippet3":::
    :::code language="vb" source="../snippets/visualbasic/VS_Snippets_Winforms/ClickOnceOnDemand/VB/Form1.vb" id="Snippet3":::

## <a name="mark-assemblies-as-optional"></a>Derlemeleri isteğe bağlı olarak işaretleme

### <a name="to-mark-assemblies-as-optional-in-your-clickonce-application-by-using-visual-studio"></a>Derlemeleri uygulamanıza isteğe bağlı olarak işaretlemek ClickOnce kullanarak Visual Studio

1. Windows Forms projesine sağ tıklayın **ve Çözüm Gezgini'a** **tıklayın.** Yayımla **sekmesini** seçin.

2. Uygulama Dosyaları **düğmesine** tıklayın.

3. için listelemeyi *ClickOnceLibrary.dll.* Yayımlama **Durumu açılan** kutusunu Dahil Edildi olarak **ayarlayın.**

4. Grup açılan **kutusunu** genişletin ve Yeni'yi **seçin.** Yeni grup `ClickOnceLibrary` adı olarak adı girin.

5. Yayımlama Sihirbazı'nı kullanarak uygulamanızı [nasıl yayımla: ClickOnce uygulama yayımlama konusunda açıklandığı gibi yayımlayın.](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)

### <a name="to-mark-assemblies-as-optional-in-your-clickonce-application-by-using-manifest-generation-and-editing-tool--graphical-client-mageuiexe"></a>Bildirim Oluşturma ve Düzenleme Aracı — Grafik İstemci (ClickOnce) kullanarak derlemeleri uygulamanıza isteğe bağlı olarak MageUI.exe

1. Bildirimlerinizi [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Adım adım [kılavuz: Uygulamanıza](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)el ile ClickOnce oluşturun.

2. Bu MageUI.exe önce, dağıtım uygulama bildirimini içeren sekmeyi seçin ve bu sekmede Dosyalar **sekmesini** seçin.

3. Uygulama ClickOnceLibrary.dll listesinde dosya türünü bulun ve Dosya Türü **sütununu** Yok olarak **ayarlayın.** Grup **sütunu için** `ClickOnceLibrary.dll` yazın.

## <a name="test-the-new-assembly"></a>Yeni derlemeyi test etmek

isteğe bağlı derlemenizi test etmek için:

1. ile dağıtılan uygulamalarınızı [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] başlatma.

2. Ana formunuz görüntülendiğinde tuşuna <xref:System.Windows.Forms.Button> basın. İleti kutusu penceresinde "Hello, World!"

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Deployment.Application.ApplicationDeployment>
