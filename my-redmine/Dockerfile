FROM redmine:3.0.0

RUN	cd /usr/src/redmine/plugins	\
	&& git clone git://github.com/suer/redmine_oauth_provider.git	\
	&& cd ..	\
	&& bundle install

RUN	/docker-entrypoint.sh rails	\
	&& rake redmine:plugins:migrate RAILS_ENV=production

ENTRYPOINT ["/docker-entrypoint.sh"]

EXPOSE 3000
CMD ["rails", "server", "-b", "0.0.0.0"]
