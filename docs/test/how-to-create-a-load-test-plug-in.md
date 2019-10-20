---
title: Yük testi eklentisi oluşturma
ms.date: 10/19/2016
ms.topic: conceptual
f1_keywords:
- vs.test.load.loadtestplugin
helpviewer_keywords:
- code, load tests
- plug-ins, load test
- load tests, plug-ins
ms.assetid: 27806972-1b15-4388-833d-6d0632816f1f
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e2eea116eb18e192720410b71136de9d823ed0fe
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72653659"
---
# <a name="how-to-create-a-load-test-plug-in"></a>Nasıl yapılır: yük testi eklentisi oluşturma

Yük testi çalışırken kodu farklı zamanlarda çalıştırmak için bir yük testi eklentisi oluşturabilirsiniz. Yük testinin yerleşik işlevlerini açmak veya değiştirmek için bir eklenti oluşturursunuz. Örneğin, yük testi çalışırken yük testi modelini ayarlamak veya değiştirmek için bir yük testi eklentisini kodda yapabilirsiniz. Bunu yapmak için <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin> arabirimini devralan bir sınıf oluşturmanız gerekir. Bu sınıfın bu arabirimin <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin.Initialize*> yöntemini uygulaması gerekir. Daha fazla bilgi için bkz. <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin>.

> [!TIP]
> Ayrıca, Web performans testleri için eklentiler de oluşturabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: Web performans testi eklentisi oluşturma](../test/how-to-create-a-web-performance-test-plug-in.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

<!-- markdownlint-disable MD003 MD020 -->
## <a name="to-create-a-load-test-plug-in-in-c"></a>' De bir yük testi eklentisi oluşturmak içinC#
<!-- markdownlint-enable MD003 MD020 -->

1. Web performans testi içeren bir Web performans ve yük testi projesi açın.

2. Test projesine bir yük testi ekleyin ve onu bir Web başarım testi çalıştıracak şekilde yapılandırın.

     Daha fazla bilgi için bkz. [hızlı başlangıç: yük testi projesi oluşturma](../test/quickstart-create-a-load-test-project.md).

3. Çözüme yeni bir **sınıf kitaplığı** projesi ekleyin. ( **Çözüm Gezgini**, çözüme sağ tıklayın ve **Ekle** ' yi seçin ve ardından **Yeni proje**' yi seçin.)

4. **Çözüm Gezgini**' de, yeni sınıf kitaplığındaki **Başvurular** klasörüne sağ tıklayın ve **Başvuru Ekle**' yi seçin.

   **Başvuru Ekle** iletişim kutusu görüntülenir.

5. **.Net** sekmesini seçin, aşağı kaydırın ve ardından **Microsoft. VisualStudio. QualityTools. LoadTestFramework**öğesini seçin.

6. **Tamam ' ı**seçin.

   **Microsoft. VisualStudio. QualityTools. LoadTestFramework** başvurusu **Çözüm Gezgini**içindeki **başvuru** klasörüne eklenir.

7. **Çözüm Gezgini**' de, Web performansı ve yük testi projesinin üst düğümüne sağ tıklayıp yük testi eklentisini eklemek istediğiniz yük testini Içerir ve **Başvuru Ekle**' yi seçin.

   **Başvuru Ekle iletişim kutusu görüntülenir**.

8. **Projeler** sekmesini seçin ve sınıf kitaplığı projesini seçin.

9. **Tamam ' ı**seçin.

10. **Kod Düzenleyicisi**'nde, <xref:Microsoft.VisualStudio.TestTools.LoadTesting> ad alanı için `using` bir ifade ekleyin.

11. Sınıf kitaplığı projesinde oluşturulan sınıf için <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin> arabirimini uygulayın. Örnek bir uygulama için aşağıdaki örnek bölümüne bakın.

12. Kodu yazdıktan sonra yeni projeyi derleyin.

13. Yük testinin üst düğümüne sağ tıklayın ve ardından **Yük testi eklentisi Ekle**' yi seçin.

     **Yük testi eklentisi Ekle** iletişim kutusu görüntülenir.

14. **Eklenti seçin**altında yük testi eklenti sınıfınızı seçin.

15. **Seçili eklenti bölmesinin Özellikler** bölümünde, çalışma zamanında kullanılacak eklentinin başlangıç değerlerini ayarlayın.

    > [!NOTE]
    > Eklentilerinizi istediğiniz kadar çok özelliği kullanıma sunabilirsiniz. bunları ortak, ayarlanabilir ve tamsayı, Boole veya dize gibi bir temel tür yapmanız yeterlidir. Web performans testi eklentisi özelliklerini daha sonra **Özellikler** penceresini kullanarak da değiştirebilirsiniz.

16. **Tamam ' ı**seçin.

     Eklenti, **Yük testi eklentileri** klasörüne eklenir.

    > [!WARNING]
    > Eklentiyi kullanan bir Web performans testi veya yük testi çalıştırdığınızda aşağıdakine benzer bir hata alabilirsiniz:
    >
    > **İstek başarısız: \<plug > olayında özel durum: dosya veya derleme ' \< "eklenti adı". dll dosyası >, sürüm = \<n. n. n. n >, kültür = neutral, PublicKeyToken = null ' veya bağımlılıklarından biri yüklenemedi. Sistem belirtilen dosyayı bulamıyor.**
    >
    > Bu, eklentilerinizin herhangi birine kod değişikliği yaptığınızda ve yeni bir DLL sürümü **(sürüm = 0.0.0.0)** oluşturuyorsanız, ancak eklentinin özgün eklenti sürümüne başvurmaya devam ediyorsa oluşur. Bu sorunu düzeltmek için aşağıdaki adımları izleyin:
    >
    > 1. Web performansı ve yük testi projenizde, başvurularda bir uyarı görürsünüz. Başvuruyu eklenti DLL 'nize kaldırın ve yeniden ekleyin.
    > 2. Testinizden veya uygun konumdan eklentiyi kaldırın ve ardından yeniden ekleyin.

## <a name="example"></a>Örnek

Aşağıdaki kod, LoadTestFinished olayı oluştuktan sonra özel kod çalıştıran bir yük testi eklentisini gösterir. Bu kod, uzak bir makinedeki bir test aracısında çalışıyorsa ve test aracısının localhost SMTP hizmeti yoksa, bir ileti kutusu açık olacağı için yük testi "devam ediyor" durumunda kalır.

> [!NOTE]
> Aşağıdaki kod, System. Windows. Forms 'a bir başvuru eklemenizi gerektirir.

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

Sekiz olay, yük testi ile özel kod çalıştırmak için yük testi eklentisinde işlenebilen bir yük testi ile ilişkilendirilir. Aşağıda yük testi çalıştırmasının farklı dönemlerine erişim sağlayan olayların bir listesi verilmiştir:

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
- [Nasıl yapılır: Web başarım testi eklentisi oluşturma](../test/how-to-create-a-web-performance-test-plug-in.md)