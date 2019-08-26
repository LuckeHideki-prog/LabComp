public class Agenda
{
    static List<CopyOfAuxiliar> agenda;
    static Scanner scanner;
    public static void main (String args[]) throws IOException{
        int opcao = -1;
        scanner = new Scanner(System.in);
        agenda = new ArrayList();
        File arquivo = new File("agendaTelefonica.csv");
        if (arquivo.exists()){
            lerArquivo();
        }
        while (opcao != 0){        
            System.out.println("Seleciona uma das opções do menu:");
            System.out.println("1- Listar CopyOfAuxiliars.");
            System.out.println("2- Adicionar novo CopyOfAuxiliar.");
            System.out.println("3- Editar CopyOfAuxiliar existente.");
            System.out.println("4- Remover CopyOfAuxiliar existente.");
            System.out.println("5- Pesquisar telefone pelo nome.");
            System.out.println("0- Finalizar programa.");
            opcao = scanner.nextInt(); 
            if (opcao > 0) executaAcao(opcao);
        }
        if (!agenda.isEmpty()){
            gravarArquivo();
        }
    }

    public static void lerArquivo() throws IOException{
        BufferedReader bufferedReader = new BufferedReader(new FileReader("agendaTelefonica.csv"));
        String linha = bufferedReader.readLine();
        int posVirgula;
        while (linha != null){
            posVirgula = linha.indexOf(";");         
            agenda.add(new CopyOfAuxiliar(linha.substring(0, posVirgula),linha.substring(posVirgula + 1)));
            linha = bufferedReader.readLine();            
        }
        bufferedReader.close();
    }

    public static void gravarArquivo() throws IOException{
        FileWriter fileWriter = new FileWriter(new File("agendaTelefonica.csv"));
        for (int i = 0; i < agenda.size(); i++){
            CopyOfAuxiliar CopyOfAuxiliar = agenda.get(i);      
            if (i > 0) fileWriter.write("\n");
            fileWriter.write(CopyOfAuxiliar.nome + ";" + CopyOfAuxiliar.telefone);
        }
        fileWriter.close();
    }

    public static void executaAcao(int opcao){
        if (agenda.isEmpty() && (opcao == 1 || opcao == 3 || opcao == 4 || opcao == 5)){
            System.out.println("A lista esta vazia.");
            return;
        }
        if (opcao == 1){
            listarCopyOfAuxiliars();
        } else if (opcao == 2){
            adicionarCopyOfAuxiliar();
        } else if (opcao == 3){
            editarCopyOfAuxiliar();
        } else if (opcao == 4){
            removerCopyOfAuxiliar();
        } else if (opcao == 5){
            procurarCopyOfAuxiliar();
        }
    }
    
    public static void procurarCopyOfAuxiliar(){
        scanner.nextLine();
        System.out.println("Digite o nome do CopyOfAuxiliar:");
        String nomePesquisado = scanner.nextLine();
        if (nomePesquisado.equals("")){
            System.out.println("Nome inválido");
            return;
        }
        int indice = retornaIndice(nomePesquisado);
        if (indice == -1){
            System.out.println("CopyOfAuxiliar não encontrado.");
            return;
        }
        
        System.out.println("O telefone deste CopyOfAuxiliar é: " + agenda.get(indice).telefone);
    }

    public static void listarCopyOfAuxiliars(){
        for (int i = 0; i < agenda.size(); i++){
            CopyOfAuxiliar CopyOfAuxiliar = agenda.get(i);
            System.out.println("Nome: " + CopyOfAuxiliar.nome + " - Telefone: " + CopyOfAuxiliar.telefone);
        }
    }

    public static void adicionarCopyOfAuxiliar(){
        scanner.nextLine();
        CopyOfAuxiliar CopyOfAuxiliar = new CopyOfAuxiliar();
        System.out.println("Digite o nome do CopyOfAuxiliar:");
        String lido = scanner.nextLine();
        if (lido != null){
            CopyOfAuxiliar.nome = lido;
        }
        System.out.println("Digite o telefone do CopyOfAuxiliar:");
        lido = scanner.nextLine();
        if (lido != null){
            CopyOfAuxiliar.telefone = lido;
        }
        agenda.add(CopyOfAuxiliar);
    }

    public static void editarCopyOfAuxiliar(){
        scanner.nextLine();
        System.out.println("Digite o nome do CopyOfAuxiliar:");
        String nomePesquisado = scanner.nextLine();
        if (nomePesquisado.equals("")){
            System.out.println("Nome inválido");
            return;
        }
        int indice = retornaIndice(nomePesquisado);
        if (indice == -1){
            System.out.println("CopyOfAuxiliar não encontrado.");
            return;
        }

        System.out.println("Selecione o que deseja alterar:");
        System.out.println("1- Nome");
        System.out.println("2- Telefone");
        int opcao = scanner.nextInt();
        scanner.nextLine();
        if (opcao == 1){
            System.out.println("Digite o novo nome: ");
            agenda.get(indice).nome = scanner.nextLine();
        } else if (opcao == 2){
            System.out.println("Digite o novo telefone: ");    
            agenda.get(indice).telefone = scanner.nextLine();        
        } else {
            System.out.println("Opção inválida.");
        }

    }

    public static void removerCopyOfAuxiliar(){
        scanner.nextLine();
        System.out.println("Digite o nome do CopyOfAuxiliar:");
        String nomePesquisado = scanner.nextLine();
        if (nomePesquisado.equals("")){
            System.out.println("Nome inválido");
            return;
        }
        int indice = retornaIndice(nomePesquisado);
        if (indice == -1){
            System.out.println("CopyOfAuxiliar não encontrado.");
            return;
        }
        try {
            agenda.remove(indice);
            System.out.println("CopyOfAuxiliar removido.");
        } catch(Exception e) {
            System.out.println("Falha na remoção do CopyOfAuxiliar. Motivo: " + e);
        }        
    }

    public static int retornaIndice(String nome){
        for (int i = 0; i < agenda.size(); i++){
            if (agenda.get(i).nome.toUpperCase().equals(nome.toUpperCase())){
                return i;
            }            
        }
        return -1;
    }
    
    public static void ordenarLista(){
        
            
        }
    }


