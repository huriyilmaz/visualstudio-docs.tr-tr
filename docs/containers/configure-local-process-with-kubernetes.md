---
title: Kubernetes ile yerel Işlem için ek yapılandırma için KubernetesLocalProcessConfig. YAML kullanma
services: azure-dev-spaces
ms.date: 07/28/2020
ms.topic: conceptual
description: KubernetesLocalProcessConfig. YAML kullanarak Kubernetes ile yerel Işlem için ek yapılandırma seçeneklerini açıklar
keywords: Kubernetes, Azure Dev Spaces, dev Spaces, Docker, Kubernetes, Azure, AKS, Azure Kubernetes hizmeti, kapsayıcılar ile yerel Işlem
monikerRange: '>=vs-2019'
author: ghogen
ms.author: ghogen
manager: jillfra
ms.openlocfilehash: 234eacedbc08007ede6bb5745a1a289aa838cccb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "87508305"
---
# <a name="configure-local-process-with-kubernetes"></a>Kubernetes ile Yerel İşlem'i yapılandırma

Bu `KubernetesLocalProcessConfig.yaml` Dosya, AKS kümenizdeki ortam değişkenlerini ve takılı dosyaları yığınlarınızın içinde çoğaltmanıza olanak sağlar. Bir dosyada aşağıdaki eylemleri belirtebilirsiniz `KubernetesLocalProcessConfig.yaml` :

* Bir birim indirin ve bu birimin yolunu ortam değişkeni olarak ayarlayın.
* Kümeniz üzerinde çalışan bir hizmetin geliştirme bilgisayarınızda çalışan süreçler için kullanılabilir olmasını sağlayın.
* Sabit bir değere sahip bir ortam değişkeni oluşturun.

Varsayılan bir `KubernetesLocalProcessConfig.yaml` dosya otomatik olarak oluşturulmaz, bu sayede dosyayı projenizin kökünde el ile oluşturmanız gerekir.

## <a name="download-a-volume"></a>Bir birimi indirin

*Env*altında, indirmek istediğiniz her birim için bir *ad* ve *değer* belirtin. *Ad* , geliştirme bilgisayarınızda kullanılacak ortam değişkenidir. *Değer* , birimin adı ve geliştirme bilgisayarınızdaki bir yoldur. *Değer* değeri *$ (volumetakal: VOLUME_NAME)/PATH/TO/FILES*biçimini alır.

Örneğin:

```yaml
version: 0.1
env:
  - name: ALLOW_LIST_PATH
    value: $(volumeMounts:allow-list)/allow-list
```

Yukarıdaki örnek, kapsayıcıdan *izin verilenler-listesi* birimini indirir ve bu konumu ve ortam değişkeninin yolunu *ALLOW_LIST_PATH*ayarlar. Varsayılan davranış, dosyaları geliştirme bilgisayarınızda geçici bir dizin altında belirttiğiniz yola indirmektir. Yukarıdaki örnekte *ALLOW_LIST_PATH* olarak ayarlanır `/TEMPORARY_DIR/allow-list` . 

> [!NOTE]
> Bir birimi indirmek, ayarladığınız yoldan bağımsız olarak bu birimin tüm içeriğini indirir. Yol yalnızca geliştirme bilgisayarında kullanılacak ortam değişkenini ayarlamak için kullanılır. Belirtecin sonuna */Allow-List* veya */Path/to/Files* eklemek, birimin nerede kalıcı olduğunu gerçekten etkilemez. Ortam değişkeni, uygulamanızın söz konusu birimin içindeki belirli bir dosyaya başvuru ihtiyacı olması durumunda yalnızca kolaylık sağlar.

Ayrıca, geçici bir dizin kullanmak yerine, birim bağlama 'yi geliştirme bilgisayarınıza indirmek için bir konum belirtme seçeneğiniz de vardır. *Birimbağlama*altında, her bir konum için bir *ad* ve *LocalPath* belirtin. *Ad* , eşleştirmek istediğiniz birim adıdır ve *LocalPath* , geliştirme bilgisayarınızdaki mutlak yoldur. Örneğin:

```yaml
version: 0.1
volumeMounts:
  - name: default-token-*
    localPath: /var/run/secrets/kubernetes.io/serviceaccount
env:
  - name: KUBERNETES_IN_CLUSTER_CONFIG_OVERRIDE
    value: $(volumeMounts:default-token-*)
```

Yukarıdaki örnek, default-Token *-1111* veya *Default-Token-1234-5678-90abcdef*gibi *varsayılan \* belirteçle*eşleşen bir birimi indirmek için *env* içindeki girişi kullanır. Birden çok birimin eşleştiği durumlarda, ilk eşleşen birim kullanılır. Tüm dosyalar, `/var/run/secrets/kubernetes.io/serviceaccount` *volumetakar*girişi kullanılarak geliştirme bilgisayarınızda öğesine indirilir. *KUBERNETES_IN_CLUSTER_CONFIG_OVERRIDE* ortam değişkeni olarak ayarlanır `/var/run/secrets/kubernetes.io/serviceaccount` .

## <a name="make-a-service-available"></a>Bir hizmeti kullanılabilir hale getirme

*Env*altında, geliştirme bilgisayarınızda kullanılabilir hale getirmek istediğiniz her bir hizmet için bir *ad* ve *değer* belirtin. *Ad* , geliştirme bilgisayarınızda kullanılacak ortam değişkenidir. *Değer* , kümenizdeki hizmetin adı ve bir yoldur. *Değer* değeri *$ (Services: SERVICE_NAME)/Path*biçimini alır.

Örneğin:

```yaml
version: 0.1
env:
  - name: MYAPP1_SERVICE_HOST
    value: $(services:myapp1)/api/v1/
```

Yukarıdaki örnek, *Myapp1* hizmetini geliştirme bilgisayarınız için kullanılabilir hale getirir ve *MYAPP1_SERVICE_HOST* ortam değişkeni, yol Ile *Myapp1* hizmetinin yerel IP adresine ayarlanır `/api/v1` (yani, `127.1.1.4/api/v1` ). *Myapp1* hizmeti, *Myapp1*veya *Myapp1. svc. Cluster. Local*ortam değişkeni kullanılarak erişilebilir.

> [!NOTE]
> Bir hizmetin geliştirme bilgisayarınızda kullanılabilir hale getirilmesi, ayarladığınız yoldan bağımsız olarak tüm hizmetin kullanılabilir olmasını sağlayacaktır. Yol yalnızca geliştirme bilgisayarında kullanılacak ortam değişkenini ayarlamak için kullanılır.
Ayrıca, *$ (Services: SERVICE_NAME kullanarak, belirli bir Kubernetes ad alanından bir hizmet yapabilirsiniz. NAMESPACE_NAME)*. Örneğin:

```yaml
version: 0.1
env:
  - name: MYAPP2_SERVICE_HOST
    value: $(services:myapp2.mynamespace)
```

Yukarıdaki *örnek,* *myapp2* ad alanından geliştirme bilgisayarınızda kullanılabilir olan ve *MYAPP2_SERVICE_HOST* ortam DEĞIŞKENINI *MyNamespace* ad alanından *myapp2* yerel IP adresine ayarlar.

## <a name="create-an-environment-variable-with-a-constant-value"></a>Sabit bir değere sahip bir ortam değişkeni oluşturun

*Env*altında, geliştirme bilgisayarınızda oluşturmak istediğiniz her ortam değişkeni için bir *ad* ve *değer* belirtin. *Ad* , geliştirme bilgisayarınızda kullanılacak ortam değişkenidir ve *değer* değeridir. Örneğin:

```yaml
version: 0.1
env:
  - name: DEBUG_MODE
    value: "true"
```

Yukarıdaki örnek, *doğru*değeri olan *DEBUG_MODE* adında bir ortam değişkeni oluşturur.

## <a name="example-kuberneteslocalprocessconfigyaml"></a>Örnek KubernetesLocalProcessConfig. YAML

Aşağıda, dosyanın tamamı için bir örnek verilmiştir `KubernetesLocalProcessConfig.yaml` :

```yaml
version: 0.1
volumeMounts:
  - name: default-token-*
    localPath: /var/run/secrets/kubernetes.io/serviceaccount
env:
  - name: KUBERNETES_IN_CLUSTER_CONFIG_OVERRIDE
    value: $(volumeMounts:default-token-*)
  - name: ALLOW_LIST_PATH
    value: $(volumeMounts:allow-list)/allow-list
  - name: MYAPP1_SERVICE_HOST
    value: $(services:myapp1)/api/v1/
  - name: MYAPP2_SERVICE_HOST
    value: $(services:myapp2.mynamespace)
  - name: DEBUG_MODE 
    value: "true"
```

## <a name="next-steps"></a>Sonraki Adımlar

Yerel geliştirme bilgisayarınıza kümenize bağlanmak için Kubernetes ile yerel Işlem kullanmaya başlamak için bkz. [Visual Studio Code Ile Kubernetes ile][local-process-kubernetes-vs-code] yerel işlem kullanma ve [Visual Studio Ile Kubernetes Ile yerel işlem kullanma][local-process-kubernetes-vs].

[local-process-kubernetes-vs-code]: https://code.visualstudio.com/docs/containers/local-process-kubernetes
[local-process-kubernetes-vs]: local-process-kubernetes.md
