---
title: Yük Testi oluşturma Plug-In
description: Yük testi çalışırken kodu farklı zamanlarda çalıştırmak için yük testi eklentisi oluşturma ve yük testinin işlevselliğini genişletme veya değiştirme hakkında bilgi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
f1_keywords:
- vs.test.load.loadtestplugin
helpviewer_keywords:
- code, load tests
- plug-ins, load test
- load tests, plug-ins
ms.assetid: 27806972-1b15-4388-833d-6d0632816f1f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.openlocfilehash: 1a29de66f87cd83b67fa688194da4f86eff5533b
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122135669"
---
# <a name="how-to-create-a-load-test-plug-in"></a>Nasıl: Yük testi eklentisi oluşturma

Yük testi çalışırken kodu farklı zamanlarda çalıştırmak için bir yük testi eklentisi oluşturabilirsiniz. Yük testinin yerleşik işlevselliğini genişletmek veya değiştirmek için bir eklenti oluşturun. Örneğin, yük testi çalışırken yük testi desenini ayarlamak veya değiştirmek için bir yük testi eklentisi kodlayabilirsiniz. Bunu yapmak için arabirimi devralan bir sınıf oluşturmanız <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin> gerekir. Bu sınıfın bu <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin.Initialize*> arabirimin yöntemini uygulaması gerekir. Daha fazla bilgi için bkz. <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin>.

> [!TIP]
> Web performans testleri için eklentiler de oluşturabilirsiniz. Daha fazla bilgi [için, bkz. How to: Create a web performance test plug-in](../test/how-to-create-a-web-performance-test-plug-in.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

<!-- markdownlint-disable MD003 MD020 -->
## <a name="to-create-a-load-test-plug-in-in-c"></a>C'de yük testi eklentisi oluşturmak için #
<!-- markdownlint-enable MD003 MD020 -->

1. Web performans testi içeren bir web performansı ve yük testi projesi açın.

2. Test projesine bir yük testi ekleyin ve web performans testi çalıştıracak şekilde yapılandırabilirsiniz.

     Daha fazla bilgi için [bkz. Hızlı Başlangıç: Yük testi projesi oluşturma.](../test/quickstart-create-a-load-test-project.md)

3. Çözüme **yeni bir Sınıf** Kitaplığı projesi ekleyin. (Çözüm Gezgini'de, çözüme sağ tıklayın ve Ekle'yi **seçin** ve ardından **Yeni** Project seçin.) 

4. Yeni **Çözüm Gezgini** kitaplığında Başvurular **klasörüne** sağ tıklayın ve Başvuru Ekle'yi **seçin.**

   Başvuru **Ekle** iletişim kutusu görüntülenir.

5. **.NET sekmesini seçin,** aşağı kaydırın ve **microsoft.VisualStudio.QualityTools.LoadTestFramework öğesini seçin.**

6. **Tamam'ı seçin.**

   **Microsoft.VisualStudio.QualityTools.LoadTestFramework** başvurusu, **Çözüm Gezgini.** 

7. Bu **Çözüm Gezgini,** yük testi eklentisini eklemek istediğiniz yük testini içeren web performansının ve yük testi projesinin en üst düğümüne sağ tıklayın ve Başvuru **Ekle'yi seçin.**

   Başvuru **Ekle iletişim kutusu görüntülenir.**

8. Projeler sekmesini **seçin** ve Sınıf Kitaplığı Project.

9. **Tamam'ı seçin.**

10. Kod **Düzenleyicisi'nde** ad alanı `using` için bir deyimi <xref:Microsoft.VisualStudio.TestTools.LoadTesting> ekleyin.

11. Sınıf <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin> Kitaplığı projesinde oluşturulan sınıf için arabirimini uygulama. Örnek uygulama için aşağıdaki Örnek bölümüne bakın.

12. Kodu yazdıktan sonra yeni projeyi derlemeniz gerekir.

13. Yük testinin üst düğümüne sağ tıklayın ve ardından Yük Testi **Eklentisi Ekle'yi seçin.**

     Yük **Testi Eklentisi Ekle iletişim** kutusu görüntülenir.

14. Eklenti **seçin altında yük** testi eklenti sınıfınızı seçin.

15. Seçili **eklentinin Özellikler bölmesinde,** eklentinin çalışma zamanında kullanmak üzere başlangıç değerlerini ayarlayın.

    > [!NOTE]
    > Eklentilerinizin istediğiniz sayıda özelliği ortaya çıkarabilirsiniz; yalnızca bunları public, settable ve Integer, Boole veya String gibi bir temel türe göre ayarlayın. Daha sonra Özellikler penceresini kullanarak web performansı testi eklentisi özelliklerini de **değiştirebilirsiniz.**

16. **Tamam'ı seçin.**

     Eklenti Yük Testi Eklentileri **klasörüne** eklenir.

    > [!WARNING]
    > Eklentinizi kullanan bir web performans testi veya yük testi çalıştırarak aşağıdakine benzer bir hata alabilirsiniz:
    >
    > **İstek başarısız oldu: Olayda özel durum: Dosya veya derleme \<plug-in> yüklenemedi ' \<"Plug-in name".dll file> , Version= , \<n.n.n.n> Culture=neutral, PublicKeyToken=null' veya bağımlılıklarından biri. Sistem belirtilen dosyayı bulamıyor.**
    >
    > Bunun nedeni, eklentilerinizin herhangi biri için kod değişiklikleri yapmak ve yeni bir DLL sürümü **(Version=0.0.0.0)** oluşturmaktır, ancak eklenti hala özgün eklenti sürümüne başvurur. Bu sorunu düzeltmek için şu adımları izleyin:
    >
    > 1. Web performansı ve yük testi projesinde başvurularda bir uyarı görüyorsunuz. Eklenti DLL'nize başvuru kaldırın ve yeniden ekleyin.
    > 2. Eklentiyi testten veya uygun konumdan kaldırın ve yeniden ekleyin.

## <a name="example"></a>Örnek

Aşağıdaki kod, Bir LoadTestFinished olayı meydana geldikten sonra özel kod çalıştıran bir yük testi eklentiyi gösterir. Bu kod uzak makinede bir test aracısı üzerinde çalıştırıldı ise ve test aracısına localhost SMTP hizmeti yoksa, bir ileti kutusu açık olduğundan yük testi "Devam ediyor" durumda kalır.

> [!NOTE]
> Aşağıdaki kod, Sistem'e bir başvuru eklemenizi gerektirir. Windows. Forms.

```csharp
using System;
using Microsoft.VisualStudio.TestTools.LoadTesting;
using System.Net.Mail;
using System.Windows.Forms;

namespace LoadTestPluginTest
{
    public class MyLoadTestPlugin : ILoadTestPlugin
    {
        LoadTest myLoadTest;

        public void Initialize(LoadTest loadTest)
        {
            myLoadTest = loadTest;
            myLoadTest.LoadTestFinished += new
                EventHandler(myLoadTest_LoadTestFinished);
        }

        void myLoadTest_LoadTestFinished(object sender, EventArgs e)
        {
            try
            {
                // place custom code here
                MailAddress MyAddress = new MailAddress("someone@example.com");
                MailMessage MyMail = new MailMessage(MyAddress, MyAddress);
                MyMail.Subject = "Load Test Finished -- Admin Email";
                MyMail.Body = myLoadTest..Name + " has finished.";

                SmtpClient MySmtpClient = new SmtpClient("localhost");
                MySmtpClient.Send(MyMail);
            }

            catch (SmtpException ex)
            {
                MessageBox.Show(ex.InnerException.Message +
                    ".\r\nMake sure you have a valid SMTP.", "LoadTestPlugin", MessageBoxButtons.OK, MessageBoxIcon.Warning, MessageBoxDefaultButton.Button1);
            }
        }
    }
}
```

Yük testiyle özel kod çalıştırmak için yük testi eklentisinde işilebilecek bir yük testiyle ilişkili sekiz olay vardır. Aşağıda, yük testi çalıştırması için farklı dönemlere erişim sağlayan olayların bir listesi yer almaktadır:

- <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest.LoadTestStarting>

- <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest.LoadTestFinished>

- <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest.LoadTestWarmupComplete>

- <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest.TestStarting>

- <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest.TestFinished>

- <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest.ThresholdExceeded>

- <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest.Heartbeat>

- <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest.LoadTestAborted>

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin>
- [Yük testleri için özel kod ve eklentiler oluşturma](../test/create-custom-code-and-plug-ins-for-load-tests.md)
- [Nasıl: Web performans testi eklentisi oluşturma](../test/how-to-create-a-web-performance-test-plug-in.md)
