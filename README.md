<<<<<<< HEAD
# testVoting
=======
# Decentralised Voting Project with Hardhat

Concernant la partie Test:

Avant les tests, nous commencons par le déploiement du contrat Voting via la fixture deployContract(), qui retourne une "instance" du contrat déployé ainsi que le owner et 5 utilisateurs dont 4 voteurs. LE 5eme n'est pas dans la liste des voteurs et permet de tester les fonctions dont l'appel est autorisé uniquement aux voteurs. 

Puis d'autre fixtures, représentant les différentes sessions, ont été crées pour simuler l'évolution du contexte du SC, chaque fixture se construit sur la précédente:
1) deployCOntract()
2)registeringVotersSession()
3)proposalSessionOpen()
4)proposalSessionClosed()
5)votingSessionOpen()
6)votingSessionClosed()

Les tests ont été répartis selon les fonctions et dans l'ordre de leur execution. Ainsi nous réalisons les tests selon l'ordre dans lequel les fonctions seront executées par les utilisateurs:
1) addVoters()
2)startProposalsRegistering()
3)addProposal() & getOneProposal()
4)endProposalsRegistering()
5)startVotingSession()
6)setVote() & getVote()
7)endVotingSession()
8)tallyVotes

Les 8 phases de tests ont été rangées sous des describes eux-mêmes rangés dans un describe général "Voting contract Tests". 

Pour chaque phase de tests on appelle la fixture, correspondante au contexte de la phase de test, combinée au Hook beforeEach. 

Bien sûr, le test qui vérifie la condition du work floxw statut est établi avant l'appel de la fixture.

Pour vérifier le ID de la proposition gagnante,  nous nous sommes placés, à l'aide la fixture endVotingSession(), dans le contexte de 4 voteurs et 2 propositions P1 et P2. P1 = 1 voix et P2 = 3 voix.

Ainsi nous arrivons avec 44 tests à un coverage de test quasi complet:  

-------------|----------|----------|----------|----------|----------------|
File         |  % Stmts | % Branch |  % Funcs |  % Lines |Uncovered Lines |
-------------|----------|----------|----------|----------|----------------|
 contracts/  |      100 |    95.83 |      100 |      100 |                |
  Voting.sol |      100 |    95.83 |      100 |      100 |                |
-------------|----------|----------|----------|----------|----------------|
All files    |      100 |    95.83 |      100 |      100 |                |
-------------|----------|----------|----------|----------|----------------|


>>>>>>> 4d05a8b (Voting smart contract tests)
