function calcularValorDaCompra(formaDePagamento, itens) {
    // Definir o cardápio com os itens e seus valores
    const cardapio = {
      cafe: 3.00,
      chantily: 1.50,
      suco: 6.20,
      sanduiche: 6.50,
      queijo: 2.00,
      salgado: 7.25,
      combo1: 9.50,
      combo2: 7.50,
    };
  
    // Definir as regras de desconto/acréscimo
    const descontoDinheiro = 0.05;
    const acrescimoCredito = 0.03;
  
    // Inicializar variáveis para o total e para checar se há itens principais
    let total = 0;
    let hasPrincipalItem = false;
  
    // Iterar pelos itens do carrinho
    for (const item of itens) {
      const [codigo, quantidade] = item.split(',');
  
      // Verificar se o código do item existe no cardápio
      if (!cardapio.hasOwnProperty(codigo)) {
        return "Item inválido!";
      }
  
      const valorItem = cardapio[codigo] * quantidade;
  
      // Verificar se é um item principal (não inclui combos)
      if (codigo !== 'combo1' && codigo !== 'combo2') {
        hasPrincipalItem = true;
      }
  
      // Verificar se há desconto para pagamento em dinheiro
      if (formaDePagamento === 'dinheiro') {
        total += valorItem * (1 - descontoDinheiro);
      } else {
        total += valorItem;
      }
    }
  
    // Verificar se há itens no carrinho
    if (itens.length === 0) {
      return "Não há itens no carrinho de compra!";
    }
  
    // Verificar se há quantidade inválida
    if (total === 0) {
      return "Quantidade inválida!";
    }
  
    // Verificar se foi pedido item extra sem o principal
    if (!hasPrincipalItem) {
      return "Item extra não pode ser pedido sem o principal";
    }
  
    // Aplicar acréscimo para pagamento a crédito
    if (formaDePagamento === 'credito') {
      total *= (1 + acrescimoCredito);
    }
  
    // Formatar o valor total da compra
    const formattedTotal = total.toFixed(2).replace('.', ',');
  
    return `R$ ${formattedTotal}`;
  }
  
  // Exemplo de uso
  const formaDePagamento = 'dinheiro';
  const itens = ['cafe,1', 'chantily,1'];
  const valorTotal = calcularValorDaCompra(formaDePagamento, itens);
  console.log(valorTotal); // Saída: "R$ 4,22"
