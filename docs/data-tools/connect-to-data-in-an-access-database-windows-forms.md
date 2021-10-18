---
title: Bir Access veritabanındaki verilere bağlanma
description: Visual Studio ' de bir erişim veritabanındaki verilere (bir. mdb dosyası veya. accdb. File) nasıl bağlanacağınızı anlayın.
ms.custom: SEO-VS-2020
ms.date: 07/18/2019
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
ms.openlocfilehash: 108e7b78319cc11ab9600017fd84990ec6c7265d
ms.sourcegitcommit: 3cfe24a74b611440b831d9591e067874c51a3bfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2021
ms.locfileid: "130087468"
---
# <a name="connect-to-data-in-an-access-database"></a>Bir Access veritabanındaki verilere bağlanma

Visual Studio kullanarak bir Access veritabanına (bir *. mdb* dosyası ya da *. accdb* dosyası) bağlanabilirsiniz. Bağlantıyı tanımladıktan sonra veriler **veri kaynakları** penceresinde görünür. Buradan, tasarım yüzeyiniz üzerine tabloları veya görünümleri sürükleyebilirsiniz.
::: moniker range=">=vs-2017"
> [!NOTE]
> Access veritabanlarına bağlanmak için Visual Studio kullanıyorsanız, Visual Studio 2022 ' den önceki Visual Studio sürümlerinin tüm 32-bit süreçler olduğunu bilmeniz gerekir.
>
> bu, Visual Studio ' deki bazı veri araçlarının yalnızca 32 bit veri sağlayıcıları kullanarak veritabanlarına erişim sağlayamayacağı anlamına gelir.

::: moniker-end

::: moniker range=">=vs-2022"
> [!NOTE]
> Access veritabanlarına bağlanmak için Visual Studio 2022 kullanıyorsanız, Visual Studio 2022 ' nin artık 64-bit işlemi olduğunu bilmeniz gerekir.
>
> bu, Visual Studio ' deki bazı veri araçlarının, 32 bit veri sağlayıcıları kullanarak veritabanlarına erişim sağlayamayacağı anlamına gelir.
>
>Access veritabanlarına bağlanan 32 bitlik uygulamaları korumanız gerekiyorsa, uygulamayı yine de Visual Studio 2022 ile derleyip çalıştırabilirsiniz. ancak, Sunucu Gezgini, veri kaynağı sihirbazı veya veri kümesi tasarımcısı gibi Visual Studio veri araçlarından birini kullanmanız gerekiyorsa, hala 32 bitlik bir işlem olan Visual Studio önceki bir sürümünü kullanmanız gerekir. 32 bitlik bir işlem olan Visual Studio son sürümü 2019 Visual Studio.
>
>Projeyi 64 bitlik bir işlem olarak dönüştürmeyi planlıyorsanız, erişim bağlantı altyapısı (ACE) olarak da adlandırılan 64 bit Microsoft Access veritabanı altyapısını kullanmanız önerilir. Lütfen bkz. [Jet için OLE DB sağlayıcısı ve ODBC sürücüsü yalnızca](/office/troubleshoot/access/jet-odbc-driver-available-32-bit-version) daha fazla bilgi için 32 bitlik sürümleridir.

::: moniker-end

## <a name="prerequisites"></a>Önkoşullar

bu yordamları kullanmak için bir Windows Forms veya WPF projesine ve bir erişim veritabanı (*. accdb* dosyası) ya da erişim 2000-2003 veritabanı (*. mdb* dosyası) gerekir. Dosya türünüze karşılık gelen yordamı izleyin.

## <a name="create-a-dataset-for-an-accdb-file"></a>. Accdb dosyası için veri kümesi oluşturma

aşağıdaki yordamı kullanarak Microsoft 365, access 2013, access 2010 veya 2007 ile oluşturulan veritabanlarına Bağlan.

1. Visual Studio ' de bir Windows Forms veya WPF uygulama projesi açın.

2. **veri kaynakları** penceresini açmak için, **görünüm** menüsünde **diğer Windows**  >  **veri kaynakları**' nı seçin.

   ![diğer Windows veri kaynaklarını görüntüleme](../data-tools/media/viewdatasources.png)

3. **Veri kaynakları** penceresinde **Yeni veri kaynağı Ekle**' ye tıklayın.

   **Veri kaynağı Yapılandırma Sihirbazı** açılır.

4. **Veri kaynağı türü seçin** sayfasında **veritabanı** ' nı seçin ve ardından **İleri**' yi seçin.

5. **Veritabanı modeli seçin** sayfasında **veri kümesi** ' ni seçin ve ardından **İleri**' yi seçin.

6. **Veri bağlantınızı seçin** sayfasında yeni **bağlantı** ' yı seçerek yeni bir veri bağlantısı yapılandırın.

   **Bağlantı ekle** iletişim kutusu açılır.

7. **Veri kaynağı** **Microsoft Access veritabanı dosyası** olarak ayarlanmamışsa, **Değiştir** düğmesini seçin.

   **Veri kaynağını Değiştir** iletişim kutusu açılır. Veri kaynakları listesinde, **Microsoft Access veritabanı dosyası**' nı seçin. **veri sağlayıcısı** açılır penceresinde **OLE DB için .NET Framework Veri Sağlayıcısı**' ni seçin ve ardından **tamam**' ı seçin.

8. **Veritabanı dosya adı**' nın **yanındaki Git ' i seçin ve** ardından *. accdb* dosyanıza gidin ve **Aç**' ı seçin.

9. Bir Kullanıcı adı ve parola girin (gerekliyse) ve ardından **Tamam**' ı seçin.

10. **Veri bağlantınızı seçin** sayfasında **İleri ' yi** seçin.

    Veri dosyasının geçerli projenizde olduğunu söyleyen bir iletişim kutusu alabilirsiniz. **Evet** veya **Hayır**' ı seçin.

11. **Bağlantı dizesini uygulama yapılandırma dosyasına kaydet** sayfasında **İleri ' yi** seçin.

12. **Veritabanı nesnelerinizi seçin** sayfasında **Tablolar** düğümünü genişletin.

13. Veri kümenize dahil etmek istediğiniz tabloları veya görünümleri seçin ve ardından **son**' u seçin.

    Veri kümesi projenize eklenir ve tablolar ve görünümler **veri kaynakları** penceresinde görünür.

## <a name="create-a-dataset-for-an-mdb-file"></a>. Mdb dosyası için veri kümesi oluşturma

aşağıdaki yordamı kullanarak Access 2000-2003 ile oluşturulan veritabanlarına Bağlan.

1. Visual Studio ' de bir Windows Forms veya WPF uygulama projesi açın.

2. **görünüm** menüsünde **diğer Windows**  >  **veri kaynakları**' nı seçin.

   ![diğer Windows veri kaynaklarını görüntüleme](../data-tools/media/viewdatasources.png)

3. **Veri kaynakları** penceresinde **Yeni veri kaynağı Ekle**' ye tıklayın.

    **Veri kaynağı Yapılandırma Sihirbazı** açılır.

4. **Veri kaynağı türü seçin** sayfasında **veritabanı** ' nı seçin ve ardından **İleri**' yi seçin.

5. **Veritabanı modeli seçin** sayfasında **veri kümesi** ' ni seçin ve ardından **İleri**' yi seçin.

6. **Veri bağlantınızı seçin** sayfasında yeni **bağlantı** ' yı seçerek yeni bir veri bağlantısı yapılandırın.

7. Veri kaynağı **Microsoft Access veritabanı dosyası (OLE DB)** değilse, **Değiştir** ' i seçerek **veri kaynağını Değiştir** Iletişim kutusunu açın ve **Microsoft Access veritabanı dosyası**' nı seçin ve ardından **Tamam**' ı seçin.

8. **Veritabanı dosyası adı**' nda, bağlanmak istediğiniz *. mdb* dosyasının yolunu ve adını belirtin ve ardından **Tamam**' ı seçin.

   ![Bağlantı erişimi veritabanı dosyası Ekle](../data-tools/media/add-connection-access-db.png)

9. **Veri bağlantınızı seçin** sayfasında **İleri ' yi** seçin.

10. **Bağlantı dizesini uygulama yapılandırma dosyasına kaydet** sayfasında **İleri ' yi** seçin.

11. **Veritabanı nesnelerinizi seçin** sayfasında **Tablolar** düğümünü genişletin.

12. Veri kümeniz içinde istediğiniz tabloları veya görünümleri seçin ve ardından **son**' u seçin.

    Veri kümesi projenize eklenir ve tablolar ve görünümler **veri kaynakları** penceresinde görünür.

## <a name="next-steps"></a>Sonraki adımlar

Yeni oluşturduğunuz veri kümesi **veri kaynakları** penceresinde kullanılabilir. Artık aşağıdaki görevlerden herhangi birini gerçekleştirebilirsiniz:

- **veri kaynakları** penceresinde öğeler ' i seçin ve bunları formunuza veya tasarım yüzeyine sürükleyin (bkz. [Windows Forms denetimleri Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md) veya [WPF veri bağlamaya genel bakış](/dotnet/desktop-wpf/data/data-binding-overview)).

- Veri kümesini oluşturan nesneleri eklemek veya düzenlemek için **veri kümesi Tasarımcısı** veri kaynağını açın.

- Veri <xref:System.Data.DataTable.ColumnChanging> <xref:System.Data.DataTable.RowChanging> kümesindeki veri tablolarının veya olayına doğrulama mantığı ekleyin (bkz. [veri kümelerinde verileri doğrulama](../data-tools/validate-data-in-datasets.md)).

## <a name="see-also"></a>Ayrıca bkz.

- [Bağlantı ekleme](../data-tools/add-new-connections.md)
- [WPF veri bağlamaya genel bakış](/dotnet/framework/wpf/data/data-binding-overview)
- [Windows Forms veri bağlama](/dotnet/framework/winforms/data-binding-and-windows-forms)
