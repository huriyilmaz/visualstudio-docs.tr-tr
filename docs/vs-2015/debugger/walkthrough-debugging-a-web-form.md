---
title: 'İzlenecek yol: Web formunda hata ayıklama | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Web pages [.NET Framework], debugging
- Web sites [.NET Framework], debugging
- ASP.NET, debugging Web applications
- Web applications [.NET Framework], debugging
- ASP.NET Web sites, debugging
- ASP.NET Web pages, debugging
- debugging ASP.NET Web applications, Web Forms
- debugging [Visual Studio], Web Forms
ms.assetid: e2b4fa14-8f5b-444d-a903-54070b784bd4
caps.latest.revision: 34
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e46169728c10d696f8dd99eb6459b9fcf081cb45
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65704926"
---
# <a name="walkthrough-debugging-a-web-form"></a>İzlenecek yol: Web Formunda Hata Ayıklama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu izlenecek yolda bulunan adımlarda [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] , Web formu olarak da bilinen bir Web uygulamasının hatalarını ayıklama işlemleri gösterilir. Yürütmeyi başlatma ve durdurma, kesme noktaları ayarlama ve **izleme** penceresinde değişkenleri inceleme işlemlerinin nasıl yapılacağını gösterir.  
  
> [!NOTE]
> Bu yönergeyi tamamlamak için sunucu bilgisayarında yönetici ayrıcalıklarına sahip olmanız gerekir. Varsayılan olarak, [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] işlem, aspnet_wp.exe veya w3wp.exe işlem olarak çalışır [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] . Hata ayıklamak için [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] , çalıştıran bilgisayarda yönetici ayrıcalıklarına sahip olmanız gerekir [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] . Daha fazla bilgi için, bkz. [System Requirements](../debugger/aspnet-debugging-system-requirements.md).  
  
 Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza veya sürümüne bağlı olarak yardım bölümünde açıklananlardan farklı bir durum içerebilir. Ayarlarınızı değiştirmek için **Araçlar** menüsünden **Içeri ve dışarı aktarma ayarları** ' nı seçin. Daha fazla bilgi için bkz. [Visual Studio 'Da geliştirme ayarlarını özelleştirme](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-create-the-web-form"></a>Web formu oluşturmak için  
  
1. Zaten açık bir çözümünüz varsa kapatın.  
  
2. **Dosya** menüsünde **Yeni**' ye ve ardından **Web sitesi**' ne tıklayın.  
  
     **Yeni Web sitesi** iletişim kutusu görüntülenir.  
  
3. **Şablonlar** bölmesinde **ASP.NET Web sitesi**' ne tıklayın.  
  
4. **Konum** satırında, listeden **http** ' ye tıklayın ve metin kutusuna yazın **http://localhost/WebSite** .  
  
5. **Dil** listesinde, **Visual C#** veya **Visual Basic**' ye tıklayın.  
  
6. **Tamam**’a tıklayın.  
  
     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Yeni bir proje oluşturur ve varsayılan HTML kaynak kodunu görüntüler. Ayrıca, IIS 'de **varsayılan Web sitesi** altında Web **sitesi** adlı yeni bir sanal dizin oluşturur.  
  
7. Alt kenar boşluğunda **Tasarım** sekmesine tıklayın.  
  
8. Sol kenar boşluğunda **araç kutusu** sekmesine tıklayın veya **Görünüm** menüsünde bunu seçin.  
  
     **Araç kutusu** açılır.  
  
9. **Araç kutusunda**, **düğme** denetimine tıklayın ve bunu ana tasarım yüzeyine, default. aspx öğesine ekleyin.  
  
10. **Araç kutusunda** **TextBox** denetimine tıklayın ve denetimi ana tasarım yüzeyine, default. aspx öğesine sürükleyin.  
  
11. Bıraktığınız düğme denetimine çift tıklayın.  
  
     Bu sizi kod sayfasına götürür: C# için Default.aspx.cs veya default. aspx. vb [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] . İmleç işlevde olmalıdır `Button1_Click` .  
  
12. `Button1_Click`İşlevinde aşağıdaki kodu ekleyin:  
  
    ```  
    ' Visual Basic  
    TextBox1.Text = "Button was clicked!"  
  
    // C#  
    TextBox1.Text = "Button was clicked!";  
    ```  
  
13. **Yapı** menüsünde **Yapı Çözümü**’ne tıklayın.  
  
     Projenin hatasız oluşturması gerekir.  
  
     Şimdi, hata ayıklamaya başlamaya hazırsınız.  
  
### <a name="to-debug-the-web-form"></a>Web formunda hata ayıklamak için  
  
1. Default.aspx.cs veya default. aspx. vb penceresinde, eklediğiniz metinle aynı satırdaki sol kenar boşluğuna tıklayın:  
  
    ```  
    ' Visual Basic  
    TextBox1.Text = "Button was clicked!"  
  
    // C#  
    textBox1.Text = "Button was clicked!";  
    ```  
  
     Kırmızı bir nokta belirir ve satırdaki metin kırmızıyla vurgulanır. Kırmızı nokta bir kesme noktası temsil eder. Uygulamayı hata ayıklayıcısı altında çalıştırdığınızda, hata ayıklayıcısı koda ulaşıldığında, yürütmeyi o konumda keser. Ardından uygulamanızın durumunu görüntüleyebilir ve ona hata ayıklama yapabilirsiniz. Daha fazla bilgi için bkz. [kesme noktaları](https://msdn.microsoft.com/fe4eedc1-71aa-4928-962f-0912c334d583).  
  
2. **Hata ayıkla** menüsünde **Hata Ayıklamayı Başlat**’a tıklayın.  
  
3. **Hata ayıklama etkin değil** iletişim kutusu görüntülenir. **Hata ayıklamayı etkinleştirmek için Web.config dosyasını Değiştir** seçeneğini belirleyin ve **Tamam**' ı tıklatın.  
  
     Internet Explorer başlatılır ve yeni tasarladığınız sayfayı görüntüler.  
  
4. Internet Explorer 'da düğmesine tıklayın.  
  
     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]' De, bu sizi sizi default.aspx.cs veya default. aspx. vb kod sayfasında kesme noktasını ayarladığınız satıra götürür. Bu satır, sarı ile vurgulanmış olmalıdır. Şimdi, uygulamanızda değişkenleri görüntüleyebilir ve yürütülmesini denetleyebilirsiniz. Uygulamanız yürütmeyi durduruyor ve bir komutun tamamlanmasını bekler.  
  
5. **Hata Ayıkla** menüsünde **Windows**' a ve ardından **Izle**' ye ve ardından **Watch1**' e tıklayın.  
  
6. **Gözcü** penceresinde **TextBox1. Text**yazın.  
  
     **Gözcü** penceresi, değişkenin değerini gösterir `TextBox1.Text` :  
  
    ```  
    ""  
    ```  
  
7. **Hata Ayıkla** menüsünde, **Atla**' ya tıklayın.  
  
     `TextBox1.Text`Okunacak **izleme** penceresindeki değişikliklerin değeri:  
  
    ```  
    "Button was clicked!"  
    ```  
  
8. **Hata Ayıkla** menüsünde **devam**' a tıklayın.  
  
9. Internet Explorer 'da, düğmeye tekrar tıklayın.  
  
     Yürütme kesme noktasında yeniden durmaktadır.  
  
10. Default.aspx.cs veya default. aspx. vb penceresinde sol kenar boşluğunda kırmızı noktaya tıklayın.  
  
     Bu, kesme noktasını kaldırır.  
  
11. **Hata ayıkla** menüsünde **Hata Ayıklamayı Durdur**’a tıklayın.  
  
### <a name="to-attach-to-the-web-form-for-debugging"></a>Hata ayıklama için Web formuna iliştirmek için  
  
1. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] içinde, hata ayıklayıcısını çalışan bir işleme ekleyebilirsiniz. En etkili hata ayıklama için yürütülebilir dosyayı sembol (PDB) dosyalarıyla hata ayıklama sürümü olarak derleyin.  
  
2. Default.aspx.cs veya default. aspx. vb penceresinde, eklediğiniz satırda bir kesme noktası ayarlamak için sol kenar boşluğuna tıklayın:  
  
    ```  
    ' Visual Basic  
    TextBox1.Text = "Button was clicked!"  
  
    // C#  
    textBox1.Text = "Button was clicked!";  
    ```  
  
3. **Hata Ayıkla** menüsünde, **hata ayıklama olmadan Başlat**' a tıklayın.  
  
     Web formu Internet Explorer altında çalışmaya başlar, ancak hata ayıklayıcı eklenmez.  
  
4. [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]İşleme iliştir. Daha fazla bilgi için bkz. [Dağıtılmış Web uygulamalarında hata ayıklama](../debugger/debugging-deployed-web-applications.md).  
  
5. Internet Explorer 'da formunuzdaki düğmeye tıklayın.  
  
     İçinde, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] default.aspx.cs, default. aspx. vb veya default. aspx içindeki kesme noktasına ulaşırsınız.  
  
6. Hata ayıklamayı bitirdiğinizde hata **Ayıkla** menüsünde, **hata ayıklamayı Durdur**' a tıklayın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ASP.NET ve AJAX Uygulamalarında Hata Ayıklama](../debugger/debugging-aspnet-and-ajax-applications.md)
