---
title: Yük Testi Eklentisi Oluşturma
ms.date: 10/19/2016
ms.topic: conceptual
f1_keywords:
- vs.test.load.loadtestplugin
helpviewer_keywords:
- code, load tests
- plug-ins, load test
- load tests, plug-ins
ms.assetid: 27806972-1b15-4388-833d-6d0632816f1f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 97952f65d78f7204410d07b90e0e538fb8499116
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589129"
---
# <a name="how-to-create-a-load-test-plug-in"></a>Nasıl yapılsın: Yük testi eklentisi oluşturma

Yük testi çalışırken kodu farklı zamanlarda çalıştırmak için bir yük testi eklentisi oluşturabilirsiniz. Yerleşik yük testinin işlevselliğini genişletmek veya değiştirmek için bir eklenti oluşturursunuz. Örneğin, yük testi çalışırken yük testi deseni ayarlamak veya değiştirmek için bir yük testi eklentisini kodlayabilirsiniz. Bunu yapmak için <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin> arabirimi devralan bir sınıf oluşturmanız gerekir. Bu sınıf bu <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin.Initialize*> arabirimin yöntemini uygulamalıdır. Daha fazla bilgi için bkz. <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin>.

> [!TIP]
> Ayrıca web performans testleri için eklentiler oluşturabilirsiniz. Daha fazla bilgi için [bkz: Web performans testi eklentisi oluşturun.](../test/how-to-create-a-web-performance-test-plug-in.md)

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

<!-- markdownlint-disable MD003 MD020 -->
## <a name="to-create-a-load-test-plug-in-in-c"></a>C'de yük testi eklentisi oluşturmak için #
<!-- markdownlint-enable MD003 MD020 -->

1. Web performans testi içeren bir web performansı ve yükleme testi projesi açın.

2. Test projesine bir yük testi ekleyin ve bir web performans testi çalıştırmak için yapılandırın.

     Daha fazla bilgi için [bkz: Quickstart: Bir yük testi projesi oluşturun.](../test/quickstart-create-a-load-test-project.md)

3. Çözüme yeni bir **Sınıf Kitaplığı** projesi ekleyin. (Çözüm **Gezgini'nde,** çözüme sağ tıklayın ve **Ekle'yi** seçin ve ardından **Yeni Proje'yi**seçin.)

4. **Çözüm Gezgini'nde,** yeni sınıf kitaplığındaki **Başvurular** klasörüne sağ tıklayın ve **Başvuru Ekle'yi**seçin.

   **Başvuru Ekle** iletişim kutusu görüntülenir.

5. **.NET** sekmesini seçin, aşağı kaydırın ve ardından **Microsoft.VisualStudio.QualityTools.LoadTestFramework'i**seçin.

6. **Tamam'ı**seçin.

   **Microsoft.VisualStudio.QualityTools.LoadTestFramework** başvurusu **Solution Explorer'daki** **Başvuru** klasörüne eklenir.

7. **Çözüm Gezgini'nde,** yük testi eklentisini eklemek istediğiniz yük testini içeren web performansı ve yük testi projesinin üst düğümünü sağ tıklatın ve **Başvuru Ekle'yi**seçin.

   **Başvuru Ekle iletişim kutusu görüntülenir.**

8. **Projeler** sekmesini seçin ve Sınıf Kitaplığı Projesi'ni seçin.

9. **Tamam'ı**seçin.

10. Kod <xref:Microsoft.VisualStudio.TestTools.LoadTesting> **Düzenleyicisi'nde,** ad alanı için bir `using` deyim ekleyin.

11. Sınıf <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin> Kitaplığı projesinde oluşturulan sınıfın arabirimini uygulayın. Örnek uygulama için aşağıdaki Örnek bölümüne bakın.

12. Kodu yazdıktan sonra yeni projeyi oluşturun.

13. Yük testinin üst düğümüne sağ tıklayın ve ardından **Yükle Testi Eklentisi Ekle'yi**seçin.

     **Yükle Testi Eklentisi** iletişim kutusu görüntülenir.

14. **Bir eklenti seç'in**altında, yük testi eklentisınıfını seçin.

15. **Seçili eklenti** bölmesinin Özellikleri'nde, eklentinin çalışma zamanında kullanması için ilk değerleri ayarlayın.

    > [!NOTE]
    > Eklentilerinizden istediğiniz kadar özellik ortaya çıkarabilirsiniz; onları herkese açık, ayarlanabilir ve Tamsayı, Boolean veya String gibi bir taban türüne ait hale getirin. Özellikler **penceresini** kullanarak web performans testi eklentiözelliklerini daha sonra değiştirebilirsiniz.

16. **Tamam'ı**seçin.

     Eklenti, **Yük Testi Eklentileri** klasörüne eklenir.

    > [!WARNING]
    > Eklentinizi kullanan bir web performans testi veya yükleme testi çalıştırdığınızda aşağıdakilere benzer bir hata alabilirsiniz:
    >
    > **İstek başarısız oldu: Eklenti> olayında \<özel durum:\<Dosya veya derleme ' "Eklenti adı".dll dosyası>, Sürüm=\<n.n.n>, Culture=neutral, PublicKeyToken=null' veya bağımlılıklarından birini yükleyemedi. Sistem belirtilen dosyayı bulamıyor.**
    >
    > Bunun nedeni, eklentilerinizden herhangi birinde kod değişiklikleri yapar ve yeni bir DLL sürümü **(Sürüm=0.0.0.0)** oluşturursanız, ancak eklenti hala orijinal eklenti sürümüne başvurur. Bu sorunu gidermek için aşağıdaki adımları izleyin:
    >
    > 1. Web performansı ve yükleme testi projenizde, başvurularda bir uyarı görürsünüz. Başvuruyu çıkarın ve eklentiniz DLL'ye yeniden ekleyin.
    > 2. Eklentiyi testinizden veya uygun konumdan çıkarın ve sonra geri ekleyin.

## <a name="example"></a>Örnek

Aşağıdaki kod, LoadTestFinished olayı gerçekleştikten sonra özel kod çalıştıran bir yük testi eklentisini gösterir. Bu kod uzak bir makinede bir test aracısı üzerinde çalıştırılırsa ve test aracısının yerel barındırma SMTP hizmeti yoksa, ileti kutusu açık olacağı için yük testi "Devam Ediyor" durumunda kalır.

> [!NOTE]
> Aşağıdaki kod, System.Windows.Forms'a bir başvuru eklemenizi gerektirir.

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

Sekiz olay, yük testi ile özel kod çalıştırmak için yük testi eklentisinde işlenebilen bir yük testi ile ilişkilidir. Aşağıda, yük testi çalışmasının farklı dönemlerine erişim sağlayan olayların bir listesi vereme

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
- [Nasıl yapilir: Web performans testi eklentisi oluşturma](../test/how-to-create-a-web-performance-test-plug-in.md)
