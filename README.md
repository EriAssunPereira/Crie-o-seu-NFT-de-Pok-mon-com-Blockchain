# Crie-o-seu-NFT-de-Pok-mon-com-Blockchain

Vamos mergulhar no mundo dos NFTs e criar um token único no padrão ERC-721 que representa um Pokémon para um jogo de batalha. Dividiremos o projeto em módulos para facilitar o entendimento e a construção do código.

### Módulo 1: Entendendo NFTs e o Padrão ERC-721
**NFTs**, ou Tokens Não Fungíveis, são ativos digitais únicos que não podem ser substituídos por outros idênticos. O padrão **ERC-721** é um protocolo na rede Ethereum que define as regras para a criação de NFTs. Cada NFT tem um identificador único e pode representar qualquer coisa, desde arte até personagens de jogos.

### Módulo 2: Configurando o Ambiente de Desenvolvimento
Para começar, você precisará configurar um ambiente de desenvolvimento Solidity. Recomenda-se usar ferramentas como **Truffle** ou **Hardhat**, que facilitam a compilação, o teste e a implantação de contratos inteligentes.

### Módulo 3: Criando o Contrato Inteligente ERC-721
Aqui está um exemplo de contrato inteligente ERC-721 que você pode usar como ponto de partida:

```solidity
pragma solidity ^0.8.0;

import "@openzeppelin/contracts/token/ERC721/ERC721.sol";
import "@openzeppelin/contracts/token/ERC721/extensions/ERC721Enumerable.sol";
import "@openzeppelin/contracts/access/Ownable.sol";

contract PokemonNFT is ERC721, ERC721Enumerable, Ownable {
    constructor() ERC721("PokemonNFT", "PNFT") {}

    // Função para criar um novo Pokémon NFT
    function mintPokemon(address to, uint256 tokenId) public onlyOwner {
        _mint(to, tokenId);
    }

    // Funções obrigatórias para sobrescrever devido ao ERC721Enumerable
    function _beforeTokenTransfer(address from, address to, uint256 tokenId)
        internal
        override(ERC721, ERC721Enumerable)
    {
        super._beforeTokenTransfer(from, to, tokenId);
    }

    function supportsInterface(bytes4 interfaceId)
        public
        view
        override(ERC721, ERC721Enumerable)
        returns (bool)
    {
        return super.supportsInterface(interfaceId);
    }
}
```

### Módulo 4: Testando o Contrato
Após escrever o contrato, você deve testá-lo localmente usando uma blockchain de teste como **Ganache**. Escreva testes automatizados para garantir que todas as funções do contrato estejam funcionando conforme esperado.

### Módulo 5: Implantando o Contrato e Criando a Interface
Depois de testar, você pode implantar o contrato na rede Ethereum. Em seguida, crie uma interface de usuário web usando **web3.js** ou **ethers.js** para permitir que os usuários interajam com o contrato, mintem novos Pokémons e visualizem os que já possuem.

### Módulo 6: Adicionando Lógica de Batalha
Para simular um jogo de batalhas, você pode expandir o contrato para incluir atributos como ataque, defesa e pontos de vida. Além disso, adicione funções que permitam que os Pokémons lutem entre si, alterando seus atributos com base no resultado da batalha.

Este é um esboço básico para começar a criar seu NFT de Pokémon com blockchain. Lembre-se de que cada Pokémon deve ser único e ter características que os diferenciem uns dos outros.
