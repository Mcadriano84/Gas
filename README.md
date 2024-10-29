# Gas

```
jsx
import React, { useState } from 'react';
import { View, Text, TextInput, Button } from 'react-native';

const App = () => {
  const [gastos, setGastos] = useState([]);
  const [valor, setValor] = useState('');
  const [categoria, setCategoria] = useState('');
  const [descricao, setDescricao] = useState('');

  const adicionarGasto = () => {
    const novoGasto = {
      data: new Date(),
      valor: parseFloat(valor),
      categoria,
      descricao,
    };
    setGastos([...gastos, novoGasto]);
    setValor('');
    setCategoria('');
    setDescricao('');
  };

  return (
    <View>
      <Text>Cadastro de Gasto</Text>
      <TextInput
        placeholder="Valor"
        value={valor}
        onChangeText={(text) => setValor(text)}
      />
      <TextInput
        placeholder="Categoria"
        value={categoria}
        onChangeText={(text) => setCategoria(text)}
      />
      <TextInput
        placeholder="Descrição"
        value={descricao}
        onChangeText={(text) => setDescricao(text)}
      />
      <Button title="Salvar" onPress={adicionarGasto} />
      <Text>Histórico de Gastos</Text>
      <FlatList
        data={gastos}
        renderItem={({ item }) => (
          <Text>
            {item.data.toLocaleDateString()} - {item.valor} - {item.categoria} -{' '}
            {item.descricao}
          </Text>
        )}
      />
    </View>
  );
};

export default 
