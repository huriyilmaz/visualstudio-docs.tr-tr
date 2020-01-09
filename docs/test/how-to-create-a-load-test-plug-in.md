---
title: Bir yük testi eklentisi oluşturma
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
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75589129"
---
# <a name="how-to-create-a-load-test-plug-in"></a>Nasıl yapılır: bir yük testi eklentisi oluşturma

Bir yük testi, yük testi çalışırken, farklı zamanlarda kodu çalıştırmak için eklenti oluşturabilirsiniz. Yerleşik yük testi işlevselliğini değiştirmenize veya üzerine genişletmek için bir eklenti oluşturun. Örneğin, ayarlamak veya yük testi çalışırken yük testi düzeni değiştirmek için bir yük testi eklentisi kod yazabilirsiniz. Bunu yapmak için devralınan bir sınıf oluşturmanız <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin> arabirimi. Bu sınıf uygulamalıdır <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin.Initialize*> bu arabirimin yöntemi. Daha fazla bilgi için bkz. <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin>.

> [!TIP]
> Web performans testleri için eklentileri de oluşturabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: Web performans testi eklentisi oluşturma](../test/how-to-create-a-web-performance-test-plug-in.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

<!-- markdownlint-disable MD003 MD020 -->
## <a name="to-create-a-load-test-plug-in-in-c"></a>' De bir yük testi eklentisi oluşturmak içinC#
<!-- markdownlint-enable MD003 MD020 -->

1. Bir web performansı ve bir web performans testi içeren bir yük testi projesi açın.

2. Bir yük testi test projesine ekleyin ve bir web performans testi çalıştırmak için yapılandırın.

     Daha fazla bilgi için [hızlı başlangıç: yük testi projesi oluşturma](../test/quickstart-create-a-load-test-project.md).

3. Çözüme yeni bir **sınıf kitaplığı** projesi ekleyin. ( **Çözüm Gezgini**, çözüme sağ tıklayın ve **Ekle** ' yi seçin ve ardından **Yeni proje**' yi seçin.)

4. İçinde **Çözüm Gezgini**, sağ **başvuruları** seçin ve yeni sınıf kitaplığı klasöründe **Başvuru Ekle**.

   **Başvuru Ekle** iletişim kutusu görüntülenir.

5. Seçin **.NET** sekmesinde, aşağı kaydırın ve ardından **gt;Microsoft.VisualStudio.QualityTools.LoadTestFramework &** .

6. **Tamam**’ı seçin.

   Başvuru **gt;Microsoft.VisualStudio.QualityTools.LoadTestFramework &** eklenir **başvuru** klasöründe **Çözüm Gezgini**.

7. İçinde **Çözüm Gezgini**web performansının üst düğümünü sağ tıklatın ve yük testi seçin ve eklentisini eklemek istediğiniz yük testini içeren test projesi yük **Başvuru Ekle**.

   **Başvuru Ekle iletişim kutusu görüntülenir**.

8. Seçin **projeleri** sekmesini ve sınıf kitaplığı Projesi'ni seçin.

9. **Tamam**’ı seçin.

10. İçinde **Kod Düzenleyicisi**, ekleme bir `using` bildirimi <xref:Microsoft.VisualStudio.TestTools.LoadTesting> ad alanı.

11. Uygulama <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin> sınıf kitaplığı projesinde oluşturulan sınıf için arabirim. Örnek uygulama için aşağıdaki örnek bölümüne bakın.

12. Kodu yazdıktan sonra yeni projeyi derleyin.

13. Yük testinin üst düğümünü sağ tıklatın ve ardından **Yük Testi Eklentisi Ekle**.

     **Yük Testi Eklentisi Ekle** iletişim kutusu görüntülenir.

14. Altında **bir eklenti seçin**seçin, yük testi eklentisi sınıfı.

15. İçinde **özelliklerini çili eklenti** bölmesinde, çalışma zamanında kullanmak eklenti için başlangıç değerlerini ayarlayın.

    > [!NOTE]
    > Eklentilerinizi istediğiniz sayıda özelliği getirebilir; bunları yalnızca genel, ayarlanabilir ve tam sayı, Boole veya dize gibi bir temel türden yapın. Ayrıca web performans testi eklentisi özelliklerini daha sonra kullanarak değiştirebileceğiniz **özellikleri** penceresi.

16. **Tamam**’ı seçin.

     Eklenti eklenir **yük testi eklentileri** klasör.

    > [!WARNING]
    > Bir web performans testi ya da eklentisini kullanan yük testi çalıştırdığınızda aşağıdakine benzer bir hata alabilirsiniz:
    >
    > **İstek başarısız: \<eklenti > olayında özel durum: dosya veya derleme '\<"eklenti adı". dll dosyası >, sürüm =\<n. n. n. n >, kültür = neutral, PublicKeyToken = null ' veya bağımlılıklarından biri yüklenemedi. Sistem belirtilen dosyayı bulamıyor.**
    >
    > Eklentilerinizi birine kod değişikliği yapmanız ve yeni bir DLL sürümü oluşturursanız Bunun nedeni **(sürüm = 0.0.0.0)** , ancak eklenti hala özgün eklenti sürümüne başvuruyor. Bu sorunu gidermek için şu adımları izleyin:
    >
    > 1. Web performansı ve yük testi projesi içinde başvurularda bir uyarı görürsünüz. Kaldırın ve Başvuruyu eklenti DLL'nizden yeniden ekleyin.
    > 2. Test veya uygun konumdan eklentiyi kaldırın ve yeniden ekleyin.

## <a name="example"></a>Örnek

Aşağıdaki kod LoadTestFinished olayı gerçekleştikten sonra özel kod çalıştıran bir yük testi eklentisi gösterir. Bir ileti kutusu açık olduğundan bu kod, uzak bir makinede test aracısı üzerinde çalıştırılan ve test aracısı localhost SMTP hizmeti yüklü olmayan, yük testi "Sürüyor" durumunda kalır.

> [!NOTE]
> Aşağıdaki kodu üzere System.Windows.Forms başvurusu eklemeniz gerekir.

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

Sekiz olayları, özel kod ile yük testi çalıştırmak için eklenti yük testinde işlenebilen bir yük testi ile ilişkilidir. Yük testi farklı sürelerde erişmeyi olaylarının bir listesi verilmiştir:

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
- [Özel kod ve yük testleri için eklentiler oluşturma](../test/create-custom-code-and-plug-ins-for-load-tests.md)
- [Nasıl yapılır: Web performans testi eklentisi oluşturma](../test/how-to-create-a-web-performance-test-plug-in.md)
