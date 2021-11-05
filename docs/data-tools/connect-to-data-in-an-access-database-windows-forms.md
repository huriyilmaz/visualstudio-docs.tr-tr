---
title: Bir Access veritabanındaki verilere bağlanma
description: Visual Studio ' de bir erişim veritabanındaki verilere (bir. mdb dosyası veya. accdb. File) nasıl bağlanacağınızı anlayın.
ms.custom: SEO-VS-2020
ms.date: 11/02/2021
ms.topic: how-to
helpviewer_keywords:
- data [Visual Studio], connecting
- connecting to data, Access databases
- Access databases, connecting
ms.assetid: 4159e815-d430-4ad0-a234-e4125fcbef18
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 335801a800bd0df15dabda447338d452bff53268
ms.sourcegitcommit: aff49629012f4d5fa07c75ea0ca5bf53d28aa173
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/05/2021
ms.locfileid: "131662399"
---
# <a name="connect-to-data-in-an-access-database"></a>Bir Access veritabanındaki verilere bağlanma

Visual Studio kullanarak bir Access veritabanına (bir *. mdb* dosyası ya da *. accdb* dosyası) bağlanabilirsiniz. Bağlantıyı tanımladıktan sonra veriler **veri kaynakları** penceresinde görünür. Buradan, tasarım yüzeyiniz üzerine tabloları veya görünümleri sürükleyebilirsiniz.
::: moniker range="vs-2017"
> [!NOTE]
> Access veritabanlarına bağlanmak için Visual Studio kullanıyorsanız, Visual Studio 2022 ' den önceki Visual Studio sürümlerinin tüm 32-bit süreçler olduğunu bilmeniz gerekir.
>
> bu, Visual Studio ' deki bazı veri araçlarının yalnızca 32 bit veri sağlayıcıları kullanarak veritabanlarına erişim sağlayamayacağı anlamına gelir.

::: moniker-end

::: moniker range=">=vs-2019"
> [!NOTE]
>Access veritabanlarına bağlanmak için Visual Studio kullanıyorsanız, Visual Studio 2022 ' den önceki Visual Studio sürümlerinin tüm 32-bit süreçler olduğunu bilmeniz gerekir. bu, Visual Studio 2019 ve önceki sürümlerde bulunan bazı veri araçlarının yalnızca 32 bit veri sağlayıcıları kullanarak veritabanlarına bağlanabilme anlamına gelir.
>
>Access veritabanlarına bağlanmak için Visual Studio 2022 kullanıyorsanız, Visual Studio 2022 ' nin artık 64-bit işlemi olduğunu bilmeniz gerekir. bu, Visual Studio ' deki bazı veri araçlarının, 32 bit veri sağlayıcıları kullanarak veritabanlarına erişim sağlayamayacağı anlamına gelir.
>
>Access veritabanlarına bağlanan 32 bitlik uygulamaları korumanız gerekiyorsa, uygulamayı yine de Visual Studio 2022 ile derleyip çalıştırabilirsiniz. ancak, Sunucu Gezgini, veri kaynağı sihirbazı veya veri kümesi tasarımcısı gibi Visual Studio veri araçlarından birini kullanmanız gerekiyorsa, hala 32 bitlik bir işlem olan Visual Studio önceki bir sürümünü kullanmanız gerekir. 32 bitlik bir işlem olan Visual Studio son sürümü 2019 Visual Studio.
>
>Projeyi 64 bitlik bir işlem olarak dönüştürmeyi planlıyorsanız, erişim bağlantı altyapısı (ACE) olarak da adlandırılan 64 bit Microsoft Access veritabanı altyapısını kullanmanız önerilir. Lütfen bkz. [Jet için OLE DB sağlayıcısı ve ODBC sürücüsü yalnızca](/office/troubleshoot/access/jet-odbc-driver-available-32-bit-version) daha fazla bilgi için 32 bitlik sürümleridir.

::: moniker-end

## <a name="prerequisites"></a>Önkoşullar

bu yordamları kullanmak için bir Windows Forms veya WPF projesine ve bir erişim veritabanı (*. accdb* dosyası) ya da erişim 2000-2003 veritabanı (*. mdb* dosyası) gerekir. Dosya türünüze karşılık gelen yordamı izleyin.

:::moniker range=">=vs-2022"
## <a name="create-a-dataset-for-an-accdb-file"></a>. Accdb dosyası için veri kümesi oluşturma

aşağıdaki yordamı kullanarak Microsoft 365, Access 2016, access 2013, access 2010 veya 2007 ile oluşturulan veritabanlarına Bağlan.

1. Visual Studio ' de bir Windows Forms veya WPF uygulama projesi açın.

2. **Veri kaynakları** penceresini açmak için **CTRL** + **Q** tuşlarına basın, arama kutusuna "veri" girin ve **veri kaynakları** penceresi ' ni seçin. ya da **görünüm** menüsünde **diğer Windows**  >  **veri kaynakları**' nı seçin. Ya da klavyede **SHIFT** + **alt** + **D** tuşlarına basın.

   ![Arama kutusundaki veri kaynaklarının ekran görüntüsü](../data-tools/media/vs-2022/view-data-sources.png)

3. **Veri kaynakları** penceresinde **Yeni veri kaynağı Ekle**' ye tıklayın.

   **Veri kaynağı Yapılandırma Sihirbazı** açılır.

   ![Veri kaynağı Yapılandırma Sihirbazı 'Nı gösteren ekran görüntüsü](media/vs-2022/data-source-configuration-wizard.png)

4. **Veri kaynağı türü seçin** sayfasında **veritabanı** ' nı seçin ve ardından **İleri**' yi seçin.

5. **Veritabanı modeli seçin** sayfasında **veri kümesi** ' ni seçin ve ardından **İleri**' yi seçin.

   ![Veritabanı modeli seçme sayfasının ekran görüntüsü](media/vs-2022/data-source-configuration-wizard-2.png)

6. **Veri bağlantınızı seçin** sayfasında yeni **bağlantı** ' yı seçerek yeni bir veri bağlantısı yapılandırın.

   ![Veri bağlantı sayfanızı seçme ekran görüntüsü](media/vs-2022/data-source-configuration-wizard-3.png)

   **Bağlantı ekle** iletişim kutusu açılır.

   ![Bağlantı Ekle iletişim kutusunun ekran görüntüsü](media/vs-2022/add-connection.png)

7. **Veri kaynağı** **Microsoft Access veritabanı dosyası** olarak ayarlanmamışsa, **Değiştir** düğmesini seçin.

   **Veri kaynağını Değiştir** iletişim kutusu açılır. Veri kaynakları listesinde, **Microsoft Access veritabanı dosyası**' nı seçin. **OLE DB için .NET Framework Veri Sağlayıcısı** seçeneği zaten önceden seçilmiş. **Tamam ' ı** seçin.

   ![Veri kaynağı seç iletişim kutusunun ekran görüntüsü](media/vs-2022/change-data-source.png)

8. **Veritabanı dosya adı**' nın **yanındaki Git ' i seçin ve** ardından *. accdb* dosyanıza gidin ve **Aç**' ı seçin.

   >[!NOTE]
   > Microsoft Office ve Visual Studio bit genişliği (32-bit veya 64 bit) eşleşmiyorsa, bir Access veritabanına bağlanırken bir hata görürsünüz. Visual Studio 2019 ' de, veritabanı sağlayıcının kaydedilmediği bir hata alırsınız. Visual Studio 2022 ' de, 32 bit veri sağlayıcısına bağlanamadan bir hata görürsünüz. bu hatayı çözmek için Office 32 bit sürümünü kullanıyorsanız Visual Studio 2019 veya daha önceki bir sürümü kullandığınızdan emin olun; Office 64 bit sürümü için Visual Studio 2022 veya üzeri bir sürüm gerekir.

9. Bir Kullanıcı adı ve parola girin (gerekliyse) ve ardından **Tamam**' ı seçin.

10. **Veri bağlantınızı seçin** sayfasında **İleri ' yi** seçin.

    Veri dosyasının geçerli projenizde olduğunu söyleyen bir iletişim kutusu alabilirsiniz. **Evet** veya **Hayır**' ı seçin.

11. **Bağlantı dizesini uygulama yapılandırma dosyasına kaydet** sayfasında **İleri ' yi** seçin.

    ![Sayfanın ekran görüntüsü](media/vs-2022/data-source-configuration-wizard-4.png)

12. **Veritabanı nesnelerinizi seçin** sayfasında **Tablolar** düğümünü genişletin.

    ![Veritabanı nesnelerinizi seçme sayfasının ekran görüntüsü](media/vs-2022/choose-your-database-objects.png)

13. Veri kümenize dahil etmek istediğiniz tabloları veya görünümleri seçin ve ardından **son**' u seçin.

    Veri kümesi projenize eklenir ve tablolar ve görünümler **veri kaynakları** penceresinde görünür.

    ![Veritabanı nesneleriyle doldurulan veri kaynakları penceresinin ekran görüntüsü](media/vs-2022/data-sources-window-populated.png)
:::moniker-end

:::moniker range="vs-2019"

## <a name="create-a-dataset-for-an-accdb-file"></a>. Accdb dosyası için veri kümesi oluşturma

aşağıdaki yordamı kullanarak Microsoft 365, Access 2016, access 2013, access 2010 veya 2007 ile oluşturulan veritabanlarına Bağlan.

1. Visual Studio ' de bir Windows Forms veya WPF uygulama projesi açın.

2. **Veri kaynakları** penceresini açmak için **CTRL** + **Q** tuşlarına basın, arama kutusuna "veri" girin ve **veri kaynakları** penceresi ' ni seçin. ya da **görünüm** menüsünde **diğer Windows**  >  **veri kaynakları**' nı seçin. Ya da klavyede **SHIFT** + **alt** + **D** tuşlarına basın.

   ![diğer Windows veri kaynaklarını görüntüleme](../data-tools/media/viewdatasources.png)

3. **Veri kaynakları** penceresinde **Yeni veri kaynağı Ekle**' ye tıklayın.

   **Veri kaynağı Yapılandırma Sihirbazı** açılır.

4. **Veri kaynağı türü seçin** sayfasında **veritabanı** ' nı seçin ve ardından **İleri**' yi seçin.

5. **Veritabanı modeli seçin** sayfasında **veri kümesi** ' ni seçin ve ardından **İleri**' yi seçin.

   ![Veritabanı modeli seçme sayfasının ekran görüntüsü](media/vs-2022/data-source-configuration-wizard-2.png)

6. **Veri bağlantınızı seçin** sayfasında yeni **bağlantı** ' yı seçerek yeni bir veri bağlantısı yapılandırın.

   ![Veri bağlantı sayfanızı seçme ekran görüntüsü](media/vs-2022/data-source-configuration-wizard-3.png)

   **Bağlantı ekle** iletişim kutusu açılır.

   ![Bağlantı Ekle iletişim kutusunun ekran görüntüsü](media/vs-2022/add-connection.png)

7. **Veri kaynağı** **Microsoft Access veritabanı dosyası** olarak ayarlanmamışsa, **Değiştir** düğmesini seçin.

   **Veri kaynağını Değiştir** iletişim kutusu açılır. Veri kaynakları listesinde, **Microsoft Access veritabanı dosyası**' nı seçin. **OLE DB için .NET Framework Veri Sağlayıcısı** seçeneği zaten önceden seçilmiş. **Tamam ' ı** seçin.

   ![Veri kaynağı seç iletişim kutusunun ekran görüntüsü](media/vs-2022/choose-data-source.png)

8. **Veritabanı dosya adı**' nın **yanındaki Git ' i seçin ve** ardından *. accdb* dosyanıza gidin ve **Aç**' ı seçin.

   >[!NOTE]
   > Microsoft Office ve Visual Studio bit genişliği (32-bit veya 64 bit) eşleşmiyorsa, bir Access veritabanına bağlanırken bir hata görürsünüz. Visual Studio 2019 ' de, veritabanı sağlayıcının kaydedilmediği bir hata alırsınız. Visual Studio 2022 ' de, 32 bit veri sağlayıcısına bağlanamadan bir hata görürsünüz. bu hatayı çözmek için Office 32 bit sürümünü kullanıyorsanız Visual Studio 2019 veya daha önceki bir sürümü kullandığınızdan emin olun; Office 64 bit sürümü için Visual Studio 2022 veya üzeri bir sürüm gerekir.

9. Bir Kullanıcı adı ve parola girin (gerekliyse) ve ardından **Tamam**' ı seçin.

10. **Veri bağlantınızı seçin** sayfasında **İleri ' yi** seçin.

    Veri dosyasının geçerli projenizde olduğunu söyleyen bir iletişim kutusu alabilirsiniz. **Evet** veya **Hayır**' ı seçin.

11. **Bağlantı dizesini uygulama yapılandırma dosyasına kaydet** sayfasında **İleri ' yi** seçin.

    ![Sayfanın ekran görüntüsü](media/vs-2022/data-source-configuration-wizard-4.png)

12. **Veritabanı nesnelerinizi seçin** sayfasında **Tablolar** düğümünü genişletin.

13. Veri kümenize dahil etmek istediğiniz tabloları veya görünümleri seçin ve ardından **son**' u seçin.

    Veri kümesi projenize eklenir ve tablolar ve görünümler **veri kaynakları** penceresinde görünür.

:::moniker-end

:::moniker range="vs-2017"

## <a name="create-a-dataset-for-an-accdb-file"></a>. Accdb dosyası için veri kümesi oluşturma

aşağıdaki yordamı kullanarak Microsoft 365, access 2013, access 2010 veya 2007 ile oluşturulan veritabanlarına Bağlan.

1. Visual Studio ' de bir Windows Forms veya WPF uygulama projesi açın.

2. **Veri kaynakları** penceresini açmak için **CTRL** + **Q** tuşlarına basın, arama kutusuna "veri" girin ve **veri kaynakları** penceresi ' ni seçin. ya da **görünüm** menüsünde **diğer Windows**  >  **veri kaynakları**' nı seçin. Veya klavyede **Shift** Alt D +  + **tuşlarına basın.**

3. Veri Kaynakları **penceresinde Yeni** Veri Kaynağı **Ekle'ye tıklayın.**

   Veri **Kaynağı Yapılandırma Sihirbazı** açılır.

4. Veri **Kaynağı** Türü **Seçin sayfasında Veritabanı'ı ve** ardından Sonraki'yi **seçin.**

5. Veritabanı **Modeli Seçin** sayfasında Veri **Kümesi'ne ve** ardından Sonraki'ye **tıklayın.**

6. Yeni bir **veri bağlantısı yapılandırmak için** Veri **Bağlantınızı Seçin** sayfasında Yeni Bağlantı'ya tıklayın.

   Bağlantı **Ekle** iletişim kutusu açılır.

7. Veri **kaynağı Microsoft** Access Veritabanı Dosyası olarak **ayarlanmazsa** Değiştir **düğmesini** seçin.

   Veri **Kaynağını Değiştir iletişim** kutusu açılır. Veri kaynakları listesinde Microsoft Access Veritabanı **Dosyası'ı seçin.** Veri sağlayıcısı **açılan listesinde,** veri sağlayıcısı için **.NET Framework Veri Sağlayıcısı'OLE DB** ve ardından Tamam'ı **seçin.**

8. Veritabanı **dosya** **adı'nın yanındaki Gözat'ı** seçin, *sonra .accdb dosyanıza* gidin ve Aç'ı **seçin.**

9. Bir kullanıcı adı ve parola girin (gerekirse) ve ardından Tamam'ı **seçin.**

10. Veri **Bağlantınızı** **seçin sayfasında Sonraki'yi** seçin.

    Veri dosyasının geçerli projeniz içinde olmadığını söyleyen bir iletişim kutusuyla karşınıza çıkabilirsiniz. Evet **veya Hayır'ı** **seçin.**

11. Bağlantı **dizesini** **Uygulama Yapılandırması dosyasına kaydet sayfasından Sonraki'yi** seçin.

12. Veritabanı **Nesnelerinizi** seçin sayfasında **Tablolar düğümünü** genişletin.

13. Veri kümenize eklemek istediğiniz tabloları veya görünümleri seçin ve ardından Son'a **seçin.**

    Veri kümesi projenize eklenir ve tablolar ve görünümler Veri Kaynakları **penceresinde** görüntülenir.

::: moniker-end

## <a name="create-a-dataset-for-an-mdb-file"></a>.mdb dosyası için veri kümesi oluşturma

Bağlan access 2000-2003 ile oluşturulan veritabanlarına aşağıdaki yordamı kullanarak erişebilirsiniz.

1. Bir Windows Forms veya WPF uygulama projesini Visual Studio.

2. Görünüm menüsünde **Diğer** Veri **Kaynakları'Windows**  >  **seçin.**

3. Veri Kaynakları **penceresinde Yeni** Veri Kaynağı **Ekle'ye tıklayın.**

    Veri **Kaynağı Yapılandırma Sihirbazı** açılır.

4. Veri **Kaynağı** Türü **Seçin sayfasında Veritabanı'ı ve** ardından Sonraki'yi **seçin.**

5. Veritabanı **Modeli Seçin** sayfasında Veri **Kümesi'ne ve** ardından Sonraki'ye **tıklayın.**

6. Yeni bir **veri bağlantısı yapılandırmak için** Veri **Bağlantınızı Seçin** sayfasında Yeni Bağlantı'ya tıklayın.

7. Veri kaynağı Microsoft Access Veritabanı Dosyası **(OLE DB)** değilse, Veri  Kaynağını Değiştir iletişim kutusunu açmak için Değiştir'i seçin ve **Microsoft Access** Veritabanı Dosyası'nın ardından Tamam'ı  **seçin.**

8. Veritabanı **dosyası adı içinde,** bağlanmak istediğiniz *.mdb* dosyasının yolunu ve adını belirtin ve ardından Tamam'ı **seçin.**

   ![Bağlantı Erişimi Veritabanı Dosyası Ekleme](../data-tools/media/add-connection-access-db.png)

9. Veri **Bağlantınızı** **seçin sayfasında Sonraki'yi** seçin.

10. Bağlantı **dizesini** **Uygulama Yapılandırması dosyasına kaydet sayfasından Sonraki'yi** seçin.

11. Veritabanı **Nesnelerinizi** seçin sayfasında **Tablolar düğümünü** genişletin.

12. Veri kümenize istediğiniz tabloları veya görünümleri seçin ve ardından Son'a **seçin.**

    Veri kümesi projenize eklenir ve tablolar ve görünümler Veri Kaynakları **penceresinde** görüntülenir.

## <a name="next-steps"></a>Sonraki adımlar

Yeni oluşturduğunuz veri kümesi, Veri Kaynakları **penceresinde** kullanılabilir. Artık aşağıdaki görevlerden herhangi birini gerçekleştirebilirsiniz:

- Veri Kaynakları penceresinde öğeleri **seçin** ve form veya tasarım yüzeyinize sürükleyin (bkz. [Windows Forms](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md) denetimlerini Visual Studio veya WPF veri [bağlamaya genel bakış).](/dotnet/desktop-wpf/data/data-binding-overview)

- Veri kümesinde veri **Veri Kümesi Tasarımcısı** nesneleri eklemek veya düzenlemek için veri kaynağını açın.

- Veri kümesinde veri tablolarının veya olayına doğrulama mantığı ekleyin <xref:System.Data.DataTable.ColumnChanging> <xref:System.Data.DataTable.RowChanging> [(bkz. Veri kümelerde verileri doğrulama).](../data-tools/validate-data-in-datasets.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Bağlantı ekleme](../data-tools/add-new-connections.md)
- [WPF veri bağlamaya genel bakış](/dotnet/framework/wpf/data/data-binding-overview)
- [Windows Form veri bağlama](/dotnet/framework/winforms/data-binding-and-windows-forms)
