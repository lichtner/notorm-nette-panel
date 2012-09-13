notorm-nette-panel
==================

NotORM Panel for Nette framework for debugging

Instalation
-----------

Into `app/bootstrap.php` after

	$container = $configurator->createContainer();

add this lines

	# connect NotORM panel

	$panel = NotORMPanel::getInstance();
	$panel->setPlatform($container->pdo->getAttribute(PDO::ATTR_DRIVER_NAME));
	\Nette\Diagnostics\Debugger::addPanel($panel);

	$container->notorm->debug = function($query, $parameters) {
		NotORMPanel::getInstance()->logQuery($query, $parameters);
	};

It is not nice but work ok ;-)


