# CollisoresUnity

# Nomes
Erick Felipe Mendes Galvez

# Atividade Collisores
Atividade passada pela orientadora Aline Firmino, Desenvolver uma cena aplicado cada um dos tipos de colisores 3D.
Devem ser utilizados todos os tipos de colisões e Triggers.

## Requisitos
Para ver essa cena é preciso o Unity com a versão 2021.3.22f1

Instalação 1.clonar o projeto 
2.Abrir o projeto no Unity.

Desenvolvimento

Para criar esse projeto foram utilizados os seguintes passos:

Criar 3 game objects 1 espera,1 cubo e uma superficie plana.

3. Criar o Script CollisionEvents.

## segue o codigo comentado e uma explicaçao rapida

Importação do Script: Adicione o script CollisionEvents.cs a um GameObject em sua cena do Unity.

Configuração de Variáveis:

FimDaSenaCanvas: Configure essa variável no Inspector do Unity para se referir ao GameObject que contém o Canvas que você deseja ativar quando um evento específico ocorre.
Eventos de Colisão:

OnCollisionEnter: Este evento é acionado quando a colisão começa.
OnCollisionExit: Este evento é acionado quando a colisão termina.
OnCollisionStay: Este evento é acionado enquanto a colisão está em andamento.

Eventos de Gatilho:

OnTriggerEnter: Este evento é acionado quando um objeto entra em um trigger.

## codigo

public GameObject FimDaSenaCanvas; 

// Este é um campo público que permite referenciar um objeto Canvas no Unity Inspector.

void OnCollisionEnter(Collision collision)
{
    if (collision.gameObject.name == "Cube")
    {
        // Este método é chamado quando um objeto colide com este objeto.
        // Verifica se o objeto que colidiu tem o nome "Cube".
        Debug.Log("Enter");
        // Registra uma mensagem de log "Enter".
        GetComponent<Renderer>().material.color = Color.red;
        // Muda a cor do objeto atual para vermelho quando uma colisão com "Cube" começa.
    }
}

void OnCollisionExit(Collision collision)
{
    if (collision.gameObject.name == "Cube")
    {
        // Este método é chamado quando a colisão com "Cube" termina.
        // Verifica se o objeto que colidiu tem o nome "Cube".
        Debug.Log("Exit");
        // Registra uma mensagem de log "Exit".
        GetComponent<Renderer>().material.color = Color.green;
        // Muda a cor do objeto atual para verde quando a colisão com "Cube" termina.
    }
}

public void FimDaCena()
{
    if (FimDaSenaCanvas != null)
    {
        // Este método é público e pode ser chamado para mostrar o Canvas associado.
        // Verifica se a variável FimDaSenaCanvas não é nula.
        FimDaSenaCanvas.SetActive(true);
        // Ativa o objeto Canvas, tornando-o visível na cena.
    }
}

void OnCollisionStay(Collision collision)
{
    if (collision.gameObject.name == "Cube")
    {
        // Este método é chamado continuamente enquanto a colisão com "Cube" está ocorrendo.
        // Verifica se o objeto que colidiu tem o nome "Cube".
        Debug.Log("Stay");
        // Registra uma mensagem de log "Stay".
        collision.transform.localEulerAngles += new Vector3(0, 0, -10) * Time.deltaTime;
        // Rotaciona o objeto que colidiu com "Cube" continuamente.
    }
}

void OnTriggerEnter(Collider trigger)
{
    if (trigger.CompareTag("esfera"))
    {
        // Este método é chamado quando um objeto com a tag "esfera" entra em um trigger.
        FimDaCena();
        // Chama o método FimDaCena para mostrar o Canvas associado.
    }
}

## Video Do unity Funcionando

https://youtu.be/8NYcW7FkrCQ

