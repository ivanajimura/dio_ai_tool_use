# Tutorial de Desenvolvimento Orientado por Testes (TDD) e pytest

Bem-vindos ao treinamento sobre Desenvolvimento Orientado por Testes (TDD) e pytest! Neste tutorial, vamos explorar os conceitos fundamentais de TDD e aprender como utilizar pytest para criar testes automatizados. Vamos usar uma abordagem de microaprendizagem para tornar o conteúdo mais acessível. 

## O que é TDD?

**Desenvolvimento Orientado por Testes (TDD)** é uma prática de desenvolvimento de software onde os testes são escritos antes do código de produção. O ciclo TDD geralmente segue estas etapas:

1. **Escrever um teste**: Crie um teste que falhe, pois a funcionalidade ainda não foi implementada.
2. **Escrever o código**: Escreva o mínimo de código necessário para passar no teste.
3. **Refatorar**: Melhore o código, garantindo que todos os testes continuem passando.

### Vantagens do TDD

- **Qualidade de código**: Resulta em um design de código mais limpo e bem estruturado.
- **Menos bugs**: Bugs são detectados mais cedo, durante a fase de desenvolvimento.
- **Manutenção facilitada**: Refatoração se torna mais segura, já que os testes garantem que a funcionalidade não foi quebrada.

## pytest: A Ferramenta de Testes

**pytest** é uma estrutura de teste em Python que facilita a escrita de testes simples e complexos. Ele é conhecido por sua simplicidade e por suas funcionalidades poderosas, como fixtures e mocks.

### Instalando pytest

Para começar, você precisa instalar o pytest. Execute o seguinte comando:

```sh
pip install pytest
```

### Escrevendo Seu Primeiro Teste

Vamos criar um simples teste de exemplo. Crie um arquivo chamado test_sample.py com o seguinte conteúdo:

```python
def func(x):
    return x + 1

def test_answer():
    assert func(3) == 5  # Este teste falhará inicialmente
```

Para rodar o teste, use o comando:

```sh
pytest
```


### Fixtures

Fixtures são funções que configuram um estado ou um contexto antes que os testes sejam executados. Elas são úteis para configurar bancos de dados, criar arquivos temporários, etc.

Exemplo de fixture:
```python
import pytest

@pytest.fixture
def input_value():
    return 39

def test_divisible_by_3(input_value):
    assert input_value % 3 == 0
```


### xfail

xfail é usado para marcar testes que são esperados falhar. Isso é útil quando você sabe que uma funcionalidade não está implementada ainda ou está em processo de correção.

Exemplo de xfail:

```python
import pytest

@pytest.mark.xfail
def test_will_fail():
    assert 1 == 2
```

### MagicMock

MagicMock é uma poderosa ferramenta do módulo unittest.mock que permite criar objetos simulados para testes. Isso é especialmente útil para testar interações com sistemas externos.

Exemplo de MagicMock:

```python
from unittest.mock import MagicMock

def test_magic_mock():
    mock = MagicMock()
    mock.method.return_value = 3
    assert mock.method() == 3
```

### Exemplos Práticos
#### Exemplo Completo com TDD

##### Escrevendo o Teste

```python
# test_calculator.py
def test_addition():
    from calculator import add
    assert add(2, 3) == 5
```

##### Escrevendo o Código

```python
# calculator.py
def add(a, b):
    return a + b
```

#####    Rodando o Teste

```sh
pytest
```

#### Exemplo de Fixture e xfail

```python
import pytest

@pytest.fixture
def sample_list():
    return [1, 2, 3, 4, 5]

@pytest.mark.xfail
def test_sum(sample_list):
    assert sum(sample_list) == 20
```

### Conclusão

Compreender e aplicar TDD junto com pytest pode aumentar significativamente a qualidade e a confiabilidade do seu código. Use fixtures para preparar estados de teste, xfail para marcar testes esperados a falhar, e MagicMock para simular comportamentos complexos. Pratique escrevendo seus próprios testes e seguindo o ciclo TDD para criar código robusto e bem testado.

Boa sorte e bons testes!