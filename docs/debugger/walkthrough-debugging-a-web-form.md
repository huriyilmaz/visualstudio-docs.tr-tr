---
title: Web Formu hata ayıklama | Microsoft Docs
description: Kesme noktaları ayarlama ve değişkenleri inceleme dahil olmak üzere ASP.NET Web uygulamasında (Web Formu) hata ayıklamayı görmek için bir izlenecek yolu izleyin.
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
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
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: e2b33685736892243fec0f00b931b811c247fa45
ms.sourcegitcommit: 8fae163333e22a673fd119e1d2da8a1ebfe0e51a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/13/2021
ms.locfileid: "129969690"
---
# <a name="walkthrough-debugging-a-web-form"></a>İzlenecek yol: Web Formunda Hata Ayıklama
Bu kılavuzda yer alan adımlar, Web Formu olarak da bilinen [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] bir Web uygulamasında hata ayıklamayı gösterir. İzleme penceresinde yürütmeyi başlatmayı ve durdurmayı, kesme noktaları ayarlamayı ve değişkenleri **incelemeyi** gösterir.

> [!NOTE]
> Bu izlenecek yolu tamamlamak için sunucu bilgisayarda Yönetici ayrıcalıklarına sahip olmanız gerekir. Varsayılan olarak, [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aspnet_wp.exe veya w3wp.exe işlem olarak [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] çalışır. hata ayıklamak [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] için, onu çalıştıran bilgisayarda Yönetici [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] ayrıcalıklarına sahip olmanız gerekir. Daha fazla bilgi için, bkz. [System Requirements](../debugger/aspnet-debugging-system-requirements.md).

Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza veya sürümünüze bağlı olarak Yardım'da açıklananlardan farklı olabilir. Ayarlarınızı değiştirmek için Araçlar menüsünde İçeri ve Dışarı  **Ayarlar'yi** seçin. Daha fazla bilgi için [bkz. Ayarları sıfırlama.](../ide/environment-settings.md#reset-settings)

## <a name="to-create-the-web-form"></a>Web Formu oluşturmak için

1. Zaten açık bir çözümünüz varsa kapatın.

2. Dosya menüsünde **Yeni** 'ye **ve ardından** Web Sitesi'ne **tıklayın.**

    Yeni **Web Sitesi iletişim** kutusu görüntülenir.

3. Şablonlar **bölmesinde Web Sitesi'ne** **ASP.NET tıklayın.**

4. Konum **satırına** listeden **HTTP'ye** tıklayın ve metin kutusuna **http://localhost/WebSite** yazın.

5. Dil listesinde **Visual**  **C# veya Visual Basic.**

6. **Tamam**'a tıklayın.

    [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] yeni bir proje oluşturur ve varsayılan HTML kaynak kodunu görüntüler. Ayrıca IIS'de Varsayılan Web Sitesi altında **WebSite** **adlı yeni bir sanal dizin** oluşturur.

7. Alt kenar **boşluğunda** Tasarım sekmesine tıklayın.

8. Sol **kenar boşluğunda** Araç Kutusu sekmesine tıklayın veya Görünüm menüsünde **bu sekmeyi** seçin.

    **Araç Kutusu** açılır.

9. Araç **Kutusunda Düğme** denetimine **tıklayın** ve default.aspx adlı ana tasarım yüzeyine ekleyin.

10. Araç **Kutusunda Metin** Kutusu **denetimine tıklayın** ve denetimi ana tasarım yüzeyine (Default.aspx) sürükleyin.

11. Bırakılan düğme denetimine çift tıklayın.

     Bu sizi C# için Default.aspx.cs veya için Default.aspx.vb kod sayfasına [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] alır. İmleç işlevinde yer alalıdır. `Button1_Click`

12. işlevine `Button1_Click` aşağıdaki kodu ekleyin:

    ```vb
    TextBox1.Text = "Button was clicked!"
    ```

    ```csharp
    TextBox1.Text = "Button was clicked!";
    ```

13. **Yapı** menüsünde **Yapı Çözümü**’ne tıklayın.

     Projenin hatasız bir şekilde derlemesi gerekir.

     Artık hata ayıklamaya başlamaya hazır oluruz.

## <a name="to-debug-the-web-form"></a>Web Formunda hata ayıklamak için

1. Default.aspx.cs veya Default.aspx.vb penceresinde, eklenen metinle aynı satırda sol kenar boşluğuna tıklayın:

   ```vb
   TextBox1.Text = "Button was clicked!"
   ```

   ```csharp
   textBox1.Text = "Button was clicked!";
   ```

    Kırmızı bir nokta belirir ve satırdaki metin kırmızıyla vurgulanır. Kırmızı nokta bir kesme noktası temsil eder. Uygulamayı hata ayıklayıcısı altında çalıştırdığınızda, hata ayıklayıcısı koda ulaşıldığında, yürütmeyi o konumda keser. Ardından uygulamanızın durumunu görüntüleyebilir ve ona hata ayıklama yapabilirsiniz. Daha fazla bilgi için [bkz. Kesme Noktaları.](/previous-versions/ktf38f66(v=vs.100))

2. **Hata ayıkla** menüsünde **Hata Ayıklamayı Başlat**’a tıklayın.

3. Hata **Ayıklama Etkinleştirilmedi** iletişim kutusu görüntülenir. Hata **ayıklamayı etkinleştirmek Web.config dosyasını değiştir'i seçin** ve Tamam'a **tıklayın.**

    Internet Explorer, yeni tasarladınız sayfayı başlatır ve görüntüler.

4. Bu Internet Explorer düğmesine tıklayın.

    içinde, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] bu sizi Default.aspx.cs veya Default.aspx.vb kod sayfasında kesme noktanızı ayar istediğiniz satıra alır. Bu satır, sarı ile vurgulanmış olmalıdır. Şimdi, uygulamanızda değişkenleri görüntüleyebilir ve yürütülmesini denetleyebilirsiniz. Uygulamanız yürütmeyi durdurur ve bir komutun sizin için beklemesini sağlar.

5. Hata **Ayıkla menüsünde,** Hata Ayıkla'Windows' ve ardından **İzle1'e**  **tıklayın.**

6. İzleme **penceresine** **TextBox1.Text yazın.**

    İzleme **penceresinde** değişkeninin değeri `TextBox1.Text` gösterilir:

   '""'

7. Hata **Ayıkla menüsünde** **AdımLa'ya tıklayın.**

    İzleme penceresinde `TextBox1.Text` okunan **değişikliklerin** değeri:

   `"Button was clicked!"`

8. Hata **Ayıkla menüsünde Devam'a** **tıklayın.**

9. Bu Internet Explorer düğmesine yeniden tıklayın.

     Yürütme kesme noktası yeniden durdurulur.

10. Default.aspx.cs veya Default.aspx.vb penceresinde, sol kenar boşluğunda kırmızı noktaya tıklayın.

     Bu işlem kesme noktası kaldırır.

11. **Hata ayıkla** menüsünde **Hata Ayıklamayı Durdur**’a tıklayın.

## <a name="to-attach-to-the-web-form-for-debugging"></a>Hata ayıklama için Web Formuna eklemek için

1. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] içinde, hata ayıklayıcısını çalışan bir işleme ekleyebilirsiniz. En etkili hata ayıklama için yürütülebilir dosyayı sembol (PDB) dosyalarıyla hata ayıklama sürümü olarak derle.

2. Default.aspx.cs veya Default.aspx.vb penceresinde sol kenar boşluğuna tıklar ve sonra da eklenen satırda bir kesme noktası ayarlayın:

   ```vb
   TextBox1.Text = "Button was clicked!"
   ```

   ```csharp
   textBox1.Text = "Button was clicked!";
   ```

3. Hata Ayıklama **menüsünde Hata** Ayıklama Olmadan **Başlat'a tıklayın.**

    Web Formu, Internet Explorer çalışmaya başlar, ancak hata ayıklayıcı ekli değildir.

4. İşleme [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] ekleme. Daha fazla bilgi için [bkz. Dağıtılan Web Uygulamalarında Hata Ayıklama.](../debugger/debugging-deployed-web-applications.md)

5. Bu Internet Explorer form üzerinde düğmesine tıklayın.

    'de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Default.aspx.cs, Default.aspx.vb veya Default.aspx'te kesme noktasıyla bağlantınız gerekir.

6. Hata ayıklamayı bitirdikten sonra Hata Ayıklama menüsünde **Hata** Ayıklamayı **Durdur'a tıklayın.**

## <a name="see-also"></a>Ayrıca bkz.

- [ASP.NET Uygulamalarında Hata Ayıklama](../debugger/how-to-enable-debugging-for-aspnet-applications.md)